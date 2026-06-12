---
title: "Trying to create an udev rule to stop card reader from being initialized"
date: 2010-01-24
forum: General Help
---

### Post by Zorael on 2010-01-24
I have a netbook (MSI Wind U100 rebrand) that has one of those card readers built into the handrest. The thing is I've never used it once, and it keeps popping up in powertop as waking the cpu when it should just shut up and be quiet.

Aside from breaking open the case and tearing it out, the immediate solution is to browse to **/sys/bus/usb/devices/usb1/1-6/** and pipe **1** to the file **remove**. That disables it until system reboot or resume, at which point I have to do it all over again.
```
$ echo 1 | sudo tee /sys/bus/usb/devices/usb1/1-6/remove
```

Now I'd like to create an udev rule to make it not get initialized at all. A quick Google search found me [this article on creating udev rules](http://reactivated.net/writing_udev_rules.html), and after toying about with the **udevadm** tool I managed to produce the attributes/properties of the device.

```
zorael@lethe:/sys/bus/usb/devices/usb1/1-6$ udevadm info -a -p $(pwd)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device     
found, all possible attributes in the udev rules key format.         
A rule to match, can be composed by the attributes of the device     
and the attributes from one single parent device.                    

  looking at device '/bus/usb/devices/usb1/1-6':
    KERNEL=="1-6"                               
    **SUBSYSTEM=="usb"**                            
    DRIVER=="usb"                               
    ATTR{configuration}=="CARD READER
    ATTR{bNumInterfaces}==" 1"                  
    ATTR{bConfigurationValue}=="1"              
    ATTR{bmAttributes}=="a0"                    
    ATTR{bMaxPower}=="500mA"                    
    ATTR{urbnum}=="3686"                        
    **ATTR{idVendor}=="0bda"**                      
    **ATTR{idProduct}=="0158"**                     
    ATTR{bcdDevice}=="5887"                     
    ATTR{bDeviceClass}=="00"                    
    ATTR{bDeviceSubClass}=="00"                 
    ATTR{bDeviceProtocol}=="00"                 
    ATTR{bNumConfigurations}=="1"               
    ATTR{bMaxPacketSize0}=="64"                 
    ATTR{speed}=="480"                          
    ATTR{busnum}=="1"                           
    ATTR{devnum}=="13"                          
    ATTR{devpath}=="6"                          
    ATTR{version}==" 2.00"                      
    ATTR{maxchild}=="0"                         
    ATTR{quirks}=="0x0"                         
    ATTR{authorized}=="1"                       
    ATTR{manufacturer}=="Generic"               
    ATTR{product}=="USB2.0-CRW"                 
    ATTR{serial}=="20071114173400000"
```

The rule I ended up with looks like this.
```
SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="0158", OPTIONS+="ignore_device", OPTIONS+="last_rule"
```

I figured that by matching the vendor and product IDs I shouldn't get any unwanted matches. The options **ignore_device** and **last_rule** are listed in the man page of udev as such;

```
*[...]*
       **OPTIONS**
           Rule and device options:

           **last_rule**
               Stops further rules application. No later rules will have any effect.

           **ignore_device**
               Ignore this event completely.

*[...]*
```

So I saved it into **/etc/udev/rules.d/**. At this point **udev test** suggests it's being read, as seen in this output (heavily cut-and-pasted out from a screen full of text);
```
zorael@lethe:/sys/bus/usb/devices/usb1/1-6$ udevadm test $(pwd)

**parse_file: reading '/etc/udev/rules.d/01-zor.cardreader.rules' as rules file**
**udev_event_execute_rules: device event will be ignored**
util_delete_path: rmdir(/dev/bus/usb/001) failed: Permission denied
udev_event_execute_rules: removed kernel created node '/dev/bus/usb/001/021'
```

Worth mentioning is that the output is much longer if I remove the rule, so at least the rule seems to be matching the device, and it seems it should work. So I thought I'd try it out.

Since I can't physically disconnect and reconnect the device (again, built into handrest), I just deauthorize the hub by piping **0** to **/sys/bus/usb/devices/usb1/authorized**. That disconnects all devices connected to it. Then I reauthorize it again by piping **1** to the same file, while at the same time monitoring udev events by running '**udev monitor --property**' in another terminal.

And lo;
```
UDEV  [1264379236.945226] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/host12/target12:0:0/12:0:0:0/block/sdb (block)                                                                                                 
UDEV_LOG=3                                                                                                        
**[COLOR="Red"]ACTION=add[/COLOR]**                                                                                                        
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/host12/target12:0:0/12:0:0:0/block/sdb                  
SUBSYSTEM=block                                                                                                   
DEVNAME=/dev/sdb
DEVTYPE=disk
SEQNUM=1971
ID_VENDOR=Generic-
ID_VENDOR_ENC=Generic-
**ID_VENDOR_ID=0bda**
ID_MODEL=Multi-Card
ID_MODEL_ENC=Multi-Card\x20\x20\x20\x20\x20\x20
**ID_MODEL_ID=0158**
ID_REVISION=1.00
ID_SERIAL=Generic-_Multi-Card_20071114173400000-0:0
ID_SERIAL_SHORT=20071114173400000
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_USB_INTERFACES=:080650:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usb-storage
ID_PATH=pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0
DKD_MEDIA_AVAILABLE=0
DKD_PRESENTATION_NOPOLICY=0
MAJOR=8
MINOR=16
DEVLINKS=/dev/block/8:16 /dev/disk/by-id/usb-Generic-_Multi-Card_20071114173400000-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:6:1.0-scsi-0:0:0:0
```

It gets added anyway. >.<

What am I doing wrong? Is **ignore_device** not the way to go? What else can I do?

---

### Post by kerneloftruth on 2010-03-10
> **Zorael said:**
> I have a netbook (MSI Wind U100 rebrand) that has one of those card readers built into the handrest. The thing is I've never used it once, and it keeps popping up in powertop as waking the cpu when it should just shut up and be quiet.

Aside from breaking open the case and tearing it out, the immediate solution is to browse to **/sys/bus/usb/devices/usb1/1-6/** and pipe **1** to the file **remove**. That disables it until system reboot or resume, at which point I have to do it all over again.
```
$ echo 1 | sudo tee /sys/bus/usb/devices/usb1/1-6/remove
```


wow - I wasn't even aware that I could simply "remove" the device :KS

I'm not using a MSI Wind but a PC from Packard Bell (Acer) to be precise the I-Power I9810GE (or: ipower G3710)

which has a built in Card Reader Bay by Realtek, too

thanks ! :D

---

### Post by cmcginty on 2010-06-06
I am trying to do the same thing for a USB camera. I worked on this for a long time, and I believe this might no longer be possible in udev. I wrote up my findings over here:

[http://superuser.com/questions/148412/remove-kernel-lock-from-unmounted-mass-storage-usb-device-from-the-command-line-i](http://superuser.com/questions/148412/remove-kernel-lock-from-unmounted-mass-storage-usb-device-from-the-command-line-i)

---


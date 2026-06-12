---
title: "Prevent USB EDGE modem mounting as a storage device"
date: 2009-10-25
forum: General Help
---

### Post by OfNoNation on 2009-10-25
I use a GSM/EDGE dongle with a mobile phone SIM (Vodophone Air card) to access the web - - - deadly slow, but it works! It has some memory on board because the Windows drivers are built in. The problem I have is that it usually gets mounted as an external storage device when it's connected, or when the machine boots up. The device appears on the desktop with it's Vodophone icon and I can't use it as a modem till I manually 'eject' it (simply unmounting doesn't do it).

Does anyone know a way to get ubuntu to totally ignore it's storage functionality, making the modem available at boot?

However, it does occasionally go staright into modem mode withouit this problem occuring, which makes no sense to me at all.

---

### Post by lswb on 2009-10-25
The drivers for a few of these devices have a paramter that can be set when the module loads. If you know the name of the driver module for the device, try the command "modinfo modulename" and see if there are any parameters that look likely. You can find out the module name by looking at the last few lines returned from the command "dmesg" right after plugging in the device. 

If that doesn't help, take a look at this link:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by OfNoNation on 2009-10-25
[FONT=Arial]Thanks for that excellent response, lswb.
I did as you suggested and came up with the following...[/FONT]

[FONT=Lucida Console][COLOR=DarkRed][I]>sudo dmesg
...
[   91.000034] Clocksource tsc unstable (delta = -295314331 ns)
[  282.826416] usb 3-2: new full speed USB device using ohci_hcd and address 2
[  283.049242] usb 3-2: configuration #1 chosen from 1 choice
[  283.138727] Initializing USB Mass Storage driver...
[  283.139115] scsi6 : SCSI emulation for USB Mass Storage devices
[  283.139327] usb-storage: device found at 2
[  283.139336] usb-storage: waiting for device to settle before scanning
[  283.139344] usbcore: registered new interface driver usb-storage
[  283.139352] USB Mass Storage support registered.
[  288.143459] usb-storage: device scan complete
[  288.150382] scsi 6:0:0:0: CD-ROM            Philips  Dev. 0 LUN 0     1.0  PQ: 0 ANSI: 0
...[/I][/COLOR][/FONT][FONT=Lucida Console][COLOR=DarkRed]
[/COLOR][/FONT] 
from which I took the module name to be 'usb-storage'.  Then...

[FONT=Lucida Console][COLOR=DarkRed][I]> sudo modinfo usb-storage
...
alias:          usb:v03EEp6901d0200dc*dsc*dp*ic*isc*ip*
alias:          usb:v03EBp2002d0100dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.28-16-generic SMP mod_unload modversions 586 
parm:           option_zero_cd:ZeroCD mode (1=Force Modem (default), 2=Allow CD-Rom (uint)
parm:           swi_tru_install:TRU-Install mode (1=Full Logic (def), 2=Force CD-Rom, 3=Force Modem) (uint)
parm:           delay_use:seconds to delay before using a new device (uint)
...[/I]
[/COLOR][/FONT] 
so I'm assuming I have to change the 'swi_tru_install' parameter to '3'... is that right?   If so, can you offer some guidance as to how it's done?

---

### Post by lswb on 2009-10-25
OK, first make sure it works. Unload the module and reload it with the Force Modem parameter:

```

sudo modprobe -r usb-storage
sudo modprobe usb-storage  swi_tru_install=3

```

You might try the "option_zero_cd=1" parameter as well if "swi_tru_install" doesn't work.

If this loads the modem properly, you can add this line to /etc/modules to make it load that way at boot.

usb-storage  swi_tru_install=3

The /etc/modules file must be edited as root. You can use "gksudo gedit /etc/modules" 

You could also use a file in /etc/modprobe.d. See "man modprobe.conf" for details.

One complication I am wondering about, that you could perhaps test and post results, is if this will interfere with other usb mass storage devices from being recognized and mounted properly. If the "swi_tru_instal=3" parameter does indeed work to recognize your modem properly, could you plug in a usb drive at the same time and see if it also works OK? If it does interfere, there are a few ways around it, but it may get a little complicated.

---

### Post by OfNoNation on 2009-10-31
&#65279;I'm afraid neither option worked.  The output I get from dmesg after first connecting the modem, then an 8GB memory stick, then 'ejecting' the mounted modem storage device is as follows. 



    [LEFT][/LEFT]
    [LEFT]# Connect modem[/LEFT]
    [LEFT][COLOR=#993300]*[   97.192050] usb 3-2: new full speed USB device using ohci_hcd and address 2*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.417918] usb 3-2: configuration #1 chosen from 1 choice*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.488939] Initializing USB Mass Storage driver...*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.489946] scsi6 : SCSI emulation for USB Mass Storage devices*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.490273] usb-storage: device found at 2*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.490281] usb-storage: waiting for device to settle before scanning*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.490292] usbcore: registered new interface driver usb-storage*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[   97.490302] USB Mass Storage support registered.*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  102.508249] usb-storage: device scan complete*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  102.515166] scsi 6:0:0:0: CD-ROM            Philips  Dev. 0 LUN 0     1.0  PQ: 0 ANSI: 0*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  102.576094] sr1: scsi-1 drive*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  102.580514] sr 6:0:0:0: Attached scsi CD-ROM sr1*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  102.580690] sr 6:0:0:0: Attached scsi generic sg2 type 5*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  106.729087] ISO 9660 Extensions: Microsoft Joliet Level 3*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  106.738098] ISOFS: changing to secondary root*[/COLOR]
[COLOR=#993300][I]
[/I][/COLOR][/LEFT]
    [LEFT][/LEFT]
    [LEFT]# Connect 8GB memory stick[/LEFT]
    [LEFT][COLOR=#993300]*[  123.116051] usb 2-2: new high speed USB device using ehci_hcd and address 3*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  123.259561] usb 2-2: configuration #1 chosen from 1 choice*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  123.260394] scsi7 : SCSI emulation for USB Mass Storage devices*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  123.300169] usb-storage: device found at 3*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  123.300178] usb-storage: waiting for device to settle before scanning*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  128.312772] usb-storage: device scan complete*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  128.314791] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.285133] sd 7:0:0:0: [sdb] 15646720 512-byte hardware sectors: (8.01 GB/7.46 GiB)*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.286611] sd 7:0:0:0: [sdb] Write Protect is off*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.286618] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.286624] sd 7:0:0:0: [sdb] Assuming drive cache: write through*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.291622] sd 7:0:0:0: [sdb] 15646720 512-byte hardware sectors: (8.01 GB/7.46 GiB)*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.292610] sd 7:0:0:0: [sdb] Write Protect is off*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.292617] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.292623] sd 7:0:0:0: [sdb] Assuming drive cache: write through*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.292639]  sdb: sdb1*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.294960] sd 7:0:0:0: [sdb] Attached SCSI removable disk*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  129.295132] sd 7:0:0:0: Attached scsi generic sg3 type 0*[/COLOR]
[COLOR=#993300][I]
[/I][/COLOR][/LEFT]
    [LEFT][/LEFT]
    [LEFT]# Eject modem[/LEFT]
    [LEFT][COLOR=#993300]*[  169.566616] usb 3-2: USB disconnect, address 2*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  169.573270] scsi 6:0:0:0: rejecting I/O to dead device*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  169.573306] scsi 6:0:0:0: rejecting I/O to dead device*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  169.573319] scsi 6:0:0:0: rejecting I/O to dead device*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  169.573353] scsi 6:0:0:0: rejecting I/O to dead device*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  172.460087] usb 3-2: new full speed USB device using ohci_hcd and address 3*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  172.684922] usb 3-2: configuration #1 chosen from 1 choice*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  172.745123] cdc_acm 3-2:1.0: ttyACM0: USB ACM device*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  172.750312] usbcore: registered new interface driver cdc_acm*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  172.750323] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  211.558613] PPP BSD Compression module registered*[/COLOR][/LEFT]
    [LEFT][COLOR=#993300]*[  211.572764] PPP Deflate Compression module registered*[/COLOR][/LEFT]
    [LEFT][/LEFT]
    [LEFT]# End

[/LEFT]
    [LEFT][/LEFT]
    [LEFT]First instance on inserting either device > ohci_hcd (/sys/bus/pci/drivers).  [/LEFT]
    [LEFT]Memeory stick is labeled 'sdb1'[/LEFT]
    [LEFT]Modem storage device is labeled 'sr1' (given CD-ROM status because it's a read only device?)  [/LEFT]
    [LEFT][/LEFT]
    [LEFT]I also installed *usb_modeswitch* and modified one of the entries in */etc/**usb_modeswitch.conf* as follows, though I couldn't find an explanation as to what should be changed in the '*MessageContent=*' line. [/LEFT]
    [LEFT][/LEFT]
    [LEFT]...[/LEFT]
    [LEFT];DefaultVendor=  [COLOR=#993300]*0x0471*[/COLOR](storage device vendor ID - Philips)[COLOR=#993300]*  *[/COLOR][/LEFT]
    [LEFT];DefaultProduct= [COLOR=#993300]*0x1210 *[/COLOR](storage device product ID)[/LEFT]
    [LEFT][/LEFT]
    [LEFT];TargetVendor=   [COLOR=#993300]*0x1dbc *[/COLOR](modem vendor ID)[/LEFT]
    [LEFT];TargetProduct=  [COLOR=#993300]*0x0005 *[/COLOR](modem product ID)[/LEFT]
    [LEFT][/LEFT]
    [LEFT]# only for reference and 0.x versions[/LEFT]
    [LEFT]# MessageEndpoint=0x05[/LEFT]
    [LEFT][/LEFT]
    [LEFT];MessageContent="55534243123456780000000000000601000000000000000000000000000000"[/LEFT]
    [LEFT]...[/LEFT]
    [LEFT][/LEFT]
    [LEFT]That didn't do it![/LEFT]
    [LEFT][/LEFT]
    [LEFT]I then added the following lines to /etc/*fstab* and it produced a 'cannot mount volume' error message and the modem wasn't activated, so I removed the line.[/LEFT]
    [LEFT]1st[/LEFT]
    [LEFT][COLOR=#993300]*/dev/sr1                                   /media/sdb1    iso9660         noauto            0  0*[/COLOR][/LEFT]
    [LEFT]then[/LEFT]
    [LEFT][COLOR=#993300]*/dev/sr1                                   /media/EDGE_MODEM   iso9660         noauto            0  0*[/COLOR]
[COLOR=#993300][I]
[/I][/COLOR][/LEFT]
    [LEFT][/LEFT]
    [LEFT]Any ideas?[/LEFT]

---

### Post by lswb on 2009-10-31
You've gone beyond my knowledge of the subject. There is a command line program "eject" that you could perhaps use in a script or udev rule to eject the storage device. I don't recall if it is included in a default install but if not you can install it from synaptic or with "apt-get install eject"

---

### Post by OfNoNation on 2009-11-03
eject is installed by default and does the trick from the command line.  My problem now is how to (a) utilise eject in a script and (b) make the script run automatically when sr1 is mounted.

Any guidance on these tasks would be greatly appreciated.

---

### Post by OfNoNation on 2009-11-03
Okay... I've written the script (eject-sr1) and it works fine... 

```

#!/bin/bash
#Eject mounted modem storage device sr1

eject sr1

```

I only need to make it run automatically when sr1 is mounted.  If I find the solution I'll report back here and mark the thread as solved.

---

### Post by lswb on 2009-11-03
The way to do it is through a udev rule. I've written a few but am not an expert, there is something of an art to it. Do some googling and see the README and help files in /lib/udev/rules.d, /etc/udev/rules.d, and /usr/share/doc/udev

---

### Post by lswb on 2009-11-03
Hi again, another way to eject the drive occurred to me that would not need a udev rule. I believe you could just put your script in /etc/network/if-pre-up.d and it will be called automatically if you use Network Manager or /etc/network/interfaces to initiate your connection. You could add some error checking, for instance to make sure the /dev/sr1 device is actually plugged and the correct one to eject, but it is probably not really necessary for this particular use.

If you like check "man interfaces" for explanation. Network Manager also makes sure that files in the /etc/netwrok/if-xxxx directories run, so it should work whether you use Network Manager or the older /etc/network/interfaces method to configure your net.

---

### Post by lswb on 2009-11-03
You know, about 10 minutes after my last post I realized that the if-pre-up.d idea was putting the cart before the horse. I guess the network interface used to make your connection is not available while /dev/sr1 is still mounted as a disk, so there wouldn't yet be any way to get the script to run before ejecting the device.

A udev rule would still work, though.

---

### Post by OfNoNation on 2009-11-03
I was just typing a response to that effect when your latest post appeared.  However... a simple solution came to me ... seeing that I only use Gnome and the modem is always plugged in when the computer is powered up, I dropped the script into Gnome's 'Startup Apps' and it boots without the device mounted. A bit windows, I know, but I can feel the headache subsiding already. Thanks for the help.

---

### Post by OfNoNation on 2009-12-16
Finally solved the problem.
I got the required information with udevadm to put together a successful udev rule.

```
udevadm info -a -p /sys/block/sr1  
 
```output:

                          ```
KERNEL=="sr1" 
     SUBSYSTEM=="block" 
     DRIVER=="" 
     ATTR{range}=="1" 
     ATTR{ext_range}=="1"  
     ATTR{removable}=="1"  
     ATTR{ro}=="0" 
     ATTR{size}=="22272" 
     ATTR{alignment_offset}=="0"  
     ATTR{capability}=="19"  
     ATTR{stat}=="      31      117      920     1488        0        0        0        0        0      964     1488"  
 
```udev rule

```
KERNEL=="sr1", ATTR{size}=="22272", LABEL=="EDGE_MODEM", SUBSYSTEM=="block", ATTR{capability}=="19", RUN+="/bin/eject-sr1"  
```Now I never see the would-be sr1.
 
I think I can sleep now!

---

### Post by lswb on 2009-12-16
Good for you! udev is pretty neat but (for me anyway) getting a working rule has always required more than a bit of experimenting. Glad you were able to get it working for your system.

---

### Post by StuartN on 2009-12-16
> **OfNoNation said:**
> I think I can sleep now!

USB_modeswitch does this, perhaps you could add your findings to their database.

---

### Post by OfNoNation on 2009-12-18
Re: USB_Modeswitch

USB Modeswitch can work in two ways (that I'm aware of); manually, by installing the binary (/usr/bin/usb_modeswitch) and the configuration file (/etc/usb_modeswitch.conf), which requires a few device-specific parameters. To get the device to switch from CD mode to modem mode, you just run 'usb_modeswitch' at the command-line.

The other method, to be used once you have achieved success manually, uses a different binary (usb_modeswitch.sh) which works with 'usb_modeswitch.tcl' and a udev rule (/etc/udev/rules.d/80-usb_modesitch.rules) to automate the process. 

It worked for me manually by configuring 'usb_modeswitch.conf' with my device's VendorID, ProductID and MessageContent, but automation was another matter. Whatever combination of the device's attributes (from 'udevadm -a -p /sys/block/sr1') I used, switching wouldn't take place.

I then decided to take usb_m's .sh & .tcl files out of the loop and get the udev rule to run /usr/bin/usb_modeswitch, which had worked for me manually.  This was a success. 

USB Modeswitch's developer, tells me that there are some devices, including mine, that are configured in such a way that they report their device class incorrectly, which causes problems with automatic switching in usb_m'.  He also told me that there is a workaround in the next release, which is scheduled for the coming weekend.

---


---
title: "Huawei Modem EC168C on Jaunty"
date: 2010-07-27
forum: General Help
---

### Post by ktofa on 2010-07-27
Hello,

I am trying to configure the Huawei USB Modem on Jaunty (9.04) and have so far hit a brick wall.

After having sifted through a fair amount of instructions , I have gotten to the stage where the modem is detected and allocated a /dev/ttyUSB0 mount point but when I try to use wvdial on the tty , I get an error 'Modem not responding'. Please see below for my wvdial.conf file
> 
Modem = /dev/ttyUSB0
Modem Type = USB Modem
Baud = 460800
Stupid Mode= 1
Phone = #777
Username = 819007
Password = 819007
New PPPD = yes


Whenever I connect the device to the PC( or start the PC with the device connected), it detects the Device as a USB Mass Storage device ( which according to read forums, should not happen on Jaunty).
 
After using the ```
 rmmod usb-storage
``` on the machine i then used the ```
sudo modprobe usbserial vendor=0x12d1 product=0x1446 
```( Ihad obtained the vendor and product information from the 'lsusb' command)

Please see below for the excerpts from the dmesg command:

> 
[   36.792837] ISO 9660 Extensions: RRIP_1991A
[   76.628780] ISO 9660 Extensions: Microsoft Joliet Level 1
[   76.633780] ISOFS: changing to secondary root
[  133.123468] usbcore: deregistering interface driver usb-storage
[  168.699744] usbcore: registered new interface driver usbserial
[  168.699760] USB Serial support registered for generic
[  168.699776] usbserial_generic 2-1:1.0: generic converter detected
[  168.699847] usb 2-1: generic converter now attached to ttyUSB0
[  168.699863] usbcore: registered new interface driver usbserial_generic
[  168.699865] usbserial: USB Serial Driver core
[  264.272043] usb 2-1: USB disconnect, address 2
[  264.272288] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  264.272302] usbserial_generic 2-1:1.0: device disconnected
[  268.864013] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  269.032078] usb 2-1: configuration #1 chosen from 1 choice
[  269.035038] usbserial_generic 2-1:1.0: generic converter detected
[  269.035094] usb 2-1: generic converter now attached to ttyUSB0
[  537.088037] usb 2-1: USB disconnect, address 3
[  537.088490] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  537.088506] usbserial_generic 2-1:1.0: device disconnected
[  543.972011] usb 2-2: new full speed USB device using uhci_hcd and address 4
[  544.140090] usb 2-2: configuration #1 chosen from 1 choice
[  544.143046] usbserial_generic 2-2:1.0: generic converter detected
[  544.143104] usb 2-2: generic converter now attached to ttyUSB0
[  743.176044] usb 2-2: USB disconnect, address 4
[  743.176523] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  743.176540] usbserial_generic 2-2:1.0: device disconnected



I also noticed that only 1 ttyUSB ( ttyUSB0) was added when i 'modprobed' the driver. Is this normal?


Please any assistance on this would be greatly appreciated.

I'll try to provide as much information as possible as quickly as possible.

---

### Post by ktofa on 2010-07-27
Nobody can help?

I have been to the following forums:
[Help 1]("http://ubuntuforums.org/showthread.php?t=1128097")
[URL="http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html"]Help 2
Help 3[/URL]

This is really important and I would truly appreciate any sort of assistance.

Thanks in anticipation.

---

### Post by ktofa on 2010-07-28
Finally got this working using the usb-modeswitch app. The modeswitch app required that I installed tcl as well as libusb ( along with its other requirements) but once that was done it worked like a charm!

Once I installed it ,I plugged in the device and it got auto-magically detected and set up.

Once that was done , I could use both wvdial and Network Manager to connect to the device.

I then had to configure routing for the connection to be usable. I used the command:


```

sudo route add default gw <remote-ip>

```

The remote ip is added to the routing tables ( but not as the default gateway ) whenever  you connect.

I hope this helps some1.

---


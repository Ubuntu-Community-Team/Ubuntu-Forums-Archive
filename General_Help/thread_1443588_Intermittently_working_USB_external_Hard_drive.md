---
title: "Intermittently working USB external Hard drive"
date: 2010-03-31
forum: General Help
---

### Post by josepaul on 2010-03-31
Hi guys, yesterday I got a new external hard drive enclosure with these specs:

[LIST]
[*]Supports Hitachi Style IDE hard disks:2.5", 9.5mm Max, 40G or less recommended
[*]High speed USB 2.0 up to 480Mbit/sec
[*]Supports USB 1.1: Up to 12Mbit/sec
[*]Plug and Play
[*]Light-weight, Aluminium alloy Construction ,shock resistant, and durable
[/LIST]

I plugged it in the first time it didn't work, then later today it worked for some reason with the exact same configuration, I thought it was working now but now when I plugged it in again its not working, the hard disk spins up each time, the hard disk is a 20Gb IDE 2.5" ext3 formatted hard drive.

My lsusb output when its working shows a usb device called litio or something, but the output now shows no usb devices. Similarly when I do sudo fdisk -l , I get the device information when its working, but when its not working, it doesnt show anything apart from the computer hard disk's filesystem information.

Another detail that might have something to do with this problem is that this drive needs 2 usb slots to work cause one usb slot doesn't provide enough power but my lsusb output seems to show I have just one USB 2.0 socket:
 
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

does this mean that the USB 1.1 socket which one of the usb cables is connected to doesn't provide enough power?

I really need this to work guys, thanks for reading

---

### Post by josepaul on 2010-03-31
BUMP  

Any ideas, guys?

---


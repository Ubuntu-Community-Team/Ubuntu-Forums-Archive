---
title: "Update firmware on usb devices"
date: 2010-11-21
forum: General Help
---

### Post by beep_gr on 2010-11-21
Hallo.

My problem is little difficult...

I want to update the firmware on some devices and I want to learn howto under linux.

The software for the upgrade is an .exe file or an .rfw one.

Usually the .exe file works fine on wine but when the program searches for the usb device, wine doesn't know where it is and I cannot continue.
I'm trying to follow the instructions at the following link;
[http://wiki.jswindle.com/index.php/Advanced_Wine_User_Installation#USB_access](http://wiki.jswindle.com/index.php/Advanced_Wine_User_Installation#USB_access) with no success...

I'll give an example for an mp3 player:
When I plug it for normal use, Linux find it as an external storage and everything is fine:

dmesg gives me:
[12421.464340] usb 2-1.4: new high speed USB device using ehci_hcd and address 16
[12421.557740] usb 2-1.4: configuration #1 chosen from 1 choice
[12421.558633] scsi7 : SCSI emulation for USB Mass Storage devices
[12421.558809] usb-storage: device found at 16
[12421.558814] usb-storage: waiting for device to settle before scanning
[12426.591963] usb-storage: device scan complete
[12426.592492] scsi 7:0:0:0: Direct-Access     ROCKCHIP USB MP3          1.00 PQ: 0 ANSI: 0
[12426.592982] scsi 7:0:0:1: Direct-Access     ROCKCHIP USB  SD          1.00 PQ: 0 ANSI: 0 CCS
[12426.594034] sd 7:0:0:0: Attached scsi generic sg4 type 0
[12426.594583] sd 7:0:0:1: Attached scsi generic sg5 type 0
[12426.603479] sd 7:0:0:0: [sdd] 3920896 512-byte logical blocks: (2.00 GB/1.86 GiB)
[12426.605063] sd 7:0:0:0: [sdd] Write Protect is off
[12426.605067] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[12426.605070] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[12426.605719] sd 7:0:0:1: [sde] Attached SCSI removable disk
[12426.607554] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[12426.607561]  sdd: sdd1
[12426.610820] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[12426.610829] sd 7:0:0:0: [sdd] Attached SCSI removable disk

and lsusb
Bus 002 Device 016: ID 071b:3203 Domain Technologies, Inc. 



Now, when I choose to connect my player to upgrade the firmware, dmesg gives me only:

[12590.020393] usb 2-1.4: new full speed USB device using ehci_hcd and address 17
[12590.112902] usb 2-1.4: configuration #1 chosen from 1 choice

and lsusb 
Bus 002 Device 016: ID 071b:3203 Domain Technologies, Inc. 





The result is that I cannot find where (and if) the kernel put the device on the /dev/ directory.

In normal conditions, kernel mount the device at /dev/sd*
When I upgrade the firmware I cannot find it...


Is there any option on kernel to capture the device or even if there is a program to upgrade the rockchip rom?

Of-course there is a solution with virtualbox but I don't want to mess with Win$ and emulators. I want to learn to upgrade under Linux...

---

### Post by Hippytaff on 2010-11-21
I just plugged in a usb device and typed mount, it shows up as being on /dev/sdb

Don't know if this helps at all? :-)

---

### Post by beep_gr on 2010-11-21
> **Hippytaff said:**
> I just plugged in a usb device and typed mount, it shows up as being on /dev/sdb

Don't know if this helps at all? :-)

Nope...

The device deactivates the main functionality and tries to find the .rfw file from pc via usb.
It's 'zombie' startup for the device... It doesn't load the hardware so it doesn't tell to pc that it is an external storage.

---


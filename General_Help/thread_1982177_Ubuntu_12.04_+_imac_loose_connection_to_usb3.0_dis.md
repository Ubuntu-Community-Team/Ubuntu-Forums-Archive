---
title: "Ubuntu 12.04 + imac loose connection to usb3.0 disk"
date: 2012-05-18
forum: General Help
---

### Post by chrisdee on 2012-05-18
Hi.

I have an 2007 imac wich I have installed Ubuntu 12.04 on.
I have a Western Digital My Passport&#8482; Essential 500GB usb 3.0 disk hooked up to one of the usb connectors on the backside of my imac.

Everytime I reboot Ubuntu I loose connection to the usb drive.
Ubuntu also sporadically loose connection with the drive without reboot.

I have to physically unplug/plug the drive for it to appare in ubuntu.

When Im at work or away from home I wonder how I can reconnect the drive remotly through commandline or similar ?

---

### Post by chrisdee on 2012-05-18
christian@t1:/var/log$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 008: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 002: ID 04f9:001a Brother Industries, Ltd HL-1430 Laser Printer
Bus 005 Device 004: ID 05ac:8206 Apple, Inc. Bluetooth HCI
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 001 Device 011: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 001 Device 012: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
christian@t1:/var/log$

---

### Post by chrisdee on 2012-05-18
christian@t1:/var/log$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4095        2047+  ee  GPT
/dev/sda2   *        4096   476110847   238053376   83  Linux
/dev/sda3       476110848   488396799     6142976   82  Linux swap / Solaris
christian@t1:/var/log$

---


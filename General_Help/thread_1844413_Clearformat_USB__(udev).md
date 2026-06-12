---
title: "Clear/format USB  (udev)"
date: 2011-09-15
forum: General Help
---

### Post by lt-mini on 2011-09-15
Hey all,

Like many other guys, I want to clean and format a usb stick.
I try to make a script for this (using perl) that this can be done automatically.


But first I make use of the udev rules to give my usb stick a name in the /dev .

[I]SUBSYSTEM=="usb", ATTRS{idVendor}=="1e3d", ATTRS{idProduct}=="2095", MODE="0666", SYMLINK+="USB_%M_%m"
[/I]

When i try to clean or format this usb stick, it always giving me errors:

For example:
1) To clean the USB stick
$  **shred -vfz /dev/USB_189_20**
shred: /dev/fr-one_189-20: pass 1/4 (random)...
shred: /dev/fr-one_189-20: error writing at offset 0: Invalid argument
 
but if i do:
$ shred -vfz /dev/sdc1

It is cleaning the USB.

2) To format the disk
$ **mkfs.vfat -F 32 -n 'Name' /dev/USB_189_20**
mkfs.vfat 3.0.9 (31 Jan 2010)
mkfs.vfat: Too few blocks for viable file system

but if i do 
$ [B]mkfs.vfat -F 32 -n 'Name' /dev/sdc1
[/B]It creates a new filesystemThe same problem for mounting.


Any of you have an idea why it won't work with the SYMLINK name from the udev rules?

Kind Regards,
mini

---

### Post by soccsddoutab on 2011-09-15
I think is good  for some one

---

### Post by dcstar on 2011-09-15
> **lt-mini said:**
> 
.........
Any of you have an idea why it won't work with the SYMLINK name from the udev rules?


Because Devices are **different** from Partitions on Devices.

---


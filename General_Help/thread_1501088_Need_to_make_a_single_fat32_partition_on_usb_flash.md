---
title: "Need to make a single fat32 partition on usb flash drive"
date: 2010-06-03
forum: General Help
---

### Post by TheNewbieGeek on 2010-06-03
Hi I am installing Debian on my netbook. I need to make a single fat32 partition on my usb flash drive. I really love linux and want it on my netbook. Thanks for the replies.

---

### Post by dabl on 2010-06-03
I must assume you have no access to a Windows computer, since that is the easy and obvious way to format a USB stick to FAT32.

So, download the ISO and make a Parted Magic Live CD:

[http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html](http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html)

It has many useful tools, including a partitioner.  With your USB stick inserted in your computer, boot the Parted Magic Live CD, choose Partitioner from the desktop, select the USB stick from the drop-down window in the upper right (don't make a mistake and pick the wrong drive!), and use the right-click menu to set a FAT32 filesystem, and then "Apply" and it will be done.

If you plan to make that a bootable USB stick, then don't forget to set the "boot" flag, again from the right-click menu on the partitioner.

---

### Post by gabak on 2010-06-03
system---administration--- disk utility

or get gparted.

both for same purpose

---

### Post by ryan858 on 2010-06-03
Command-line Method:

You can use fdisk or cfdisk to create the nessesary partition(s), then use mkfs.vfat to format it... I think you can specify whether it's FAT32 or FAT16, etc. You should ***man mkfs.vfat***.

---

### Post by TheNewbieGeek on 2010-06-03
Hello I would like to do it with the terminal command prompt. Can you help me? I know what you mean by the commands but when I choose fdisk for example it is not enough. How do I tell it to fdisk my usb flash drive.

---


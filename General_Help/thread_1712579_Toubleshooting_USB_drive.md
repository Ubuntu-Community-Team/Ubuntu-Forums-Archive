---
title: "Toubleshooting USB drive"
date: 2011-03-22
forum: General Help
---

### Post by muchavez on 2011-03-22
Hey guys, brand new ubuntu user here,  I tried loading a usb drive into my computer and I think there may be a setting that I need to configure.  When I tried loading ubuntu on my brothers computer I was able to plug it in and the device popped up on the desktop, however when I try loading the device on my computer, I think it gets mounted however it does not appear on the screen

when I type sudo fdisk -l i get

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14212   114149376   83  Linux
/dev/sda2           14212       14594     3068929    5  Extended
/dev/sda5           14212       14594     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 3998 MB, 3998220288 bytes
49 heads, 49 sectors/track, 3252 cylinders
Units = cylinders of 2401 * 512 = 1229312 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4        3253     3900480    c  W95 FAT32 (LBA) <--USB drive?

Thanks for your time =]

---

### Post by Mark Phelps on 2011-03-23
When you removed the device from your brother's PC, did you just unplug it? Or did you do the safe removal stuff, first?

If you just unplugged it, that may have left the filesystem in a "dirty" state -- in which case, you may have to plug it into a Windows PC and run CHKDSK on it.

---

### Post by muchavez on 2011-03-23
Oh, no these are 2 different usb drives, However I will check the drive when I get home from work.  Is there any command that I can use through terminal to get the the USB drive?

---

### Post by muchavez on 2011-03-24
I double checked the USB drive and it seems to be fine. any other suggestions?  Is there a way to get to the USB drive through the terminal?

---


---
title: "Remove one of two grub loaders"
date: 2009-09-05
forum: General Help
---

### Post by Joshag on 2009-09-05
Some time ago I started loading Ubuntu 9.04 on my sons desktop but the load failed (never started) because of video driver issues. This forever left a grub menu with two options: windows xp / ubuntu. 
I never worried much about it because it defaulted to windows and did not cause a problem. I did try and repair the mbr with windows installation disk but to no avail. I was always left with the grub menu.

I recently loaded ubuntu 9.04 again (video problem resolved) and the installation took but............ I now have two grub loaders. The first, the one I would expect after ubuntu install, and the second which was left from the first attempt. 

Pain in the butt. To enter windows you have to select from both menus.

Is there a way to remove the second loader? And if not remove at least edit? The second menu has a 24 second clock that I could at least change to 0 or 1.

---

### Post by Liolikas on 2009-09-05
Strange how this can happen.
Show fdisk -l
Means you have two /boot folders...
Show your /boot/grub/menu.lst too.

---

### Post by Joshag on 2009-09-05
Sorry for the delay. Wicked electrical storms have been playing hell with my routers.

Here goes:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03780377

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e78af6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         393     3156741    5  Extended
/dev/sdb2             394       19457   153131580   83  Linux
/dev/sdb5               2         393     3148740   82  Linux swap / Solaris

It has been edited to remove some of the older kernel options and placed widows on top of list.

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4b1f2983-c5b4-467d-ade7-229942e0d582
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4b1f2983-c5b4-467d-ade7-229942e0d582 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		4b1f2983-c5b4-467d-ade7-229942e0d582
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4b1f2983-c5b4-467d-ade7-229942e0d582 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		4b1f2983-c5b4-467d-ade7-229942e0d582
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Joshag on 2009-09-07
Problem solved. 
Second grub loader was windows boot.ini. I edited it to remove umbuntu and changed menu timeout to 0.

---


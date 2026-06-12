---
title: "Please help me recover some data from raid 0"
date: 2010-08-11
forum: General Help
---

### Post by aznpunkerboy on 2010-08-11
So I've pulled two hard drives out of my busted windows xp system (dead mb) and I'm trying to get some data off of them.  The drives are in raid 0, so my friend told me that I might be able to do something if I use linux.  Some late night searching on the internet directed me to a few resources, one of which was this forum.  I've tried 2 methods, neither of which have worked.

1. mdadm

ubuntu@ubuntu:~$ sudo mdadm --detail /dev/sdb
mdadm: /dev/sdb does not appear to be an md device

2. dmraid

ubuntu@ubuntu:~$ sudo dmraid -s
/dev/sdb: "sil" and "hpt45x" formats discovered (using hpt45x)!
ERROR: sil: wrong # of devices in RAID set "sil_agafdhcebccj" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "sil_agafdhcebccj"
ERROR: no RAID set found

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: "sil" and "hpt45x" formats discovered (using hpt45x)!
/dev/sda: sil, "sil_agafdhcebccj", stripe, ok, 390718880 sectors, data@ 0
/dev/sdb: hpt45x, "hpt45x_SPARE", spare, ok, 390721957 sectors, data@ 0

Help please?  I've got some files for work that I'd really like to get off there.  I've played with unix a bit in college and I've ran ubuntu before, but usually using the GUI, so a lot of this stuff is over my head.  But from what I gather, my system thinks that one of the drives isn't a raid drive?  Please tell me I'm wrong, and that there's something I can do to get the data back.  Otherwise, I'm going to be sad.

---

### Post by aznpunkerboy on 2010-08-11
Don't know if this helps, but here's some more info

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08e808e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 8111 MB, 8111783936 bytes
90 heads, 26 sectors/track, 6770 cylinders
Units = cylinders of 2340 * 512 = 1198080 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x091c41da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           4        6771     7917632    b  W95 FAT32

I'm running ubuntu off a usb drive right now, /dev/sdc1, the other 2 are the raid drives.

---

### Post by Quackers on 2010-08-12
I'm afraid I can't give you any specific advice, but I can say that on my Googling travels I have come across posts that give details on how recovery can be achieved from radi 0 discs. Good luck

---


---
title: "Unable to mount drives"
date: 2010-08-08
forum: General Help
---

### Post by lyonesse9 on 2010-08-08
Hi I am totally new with linux.

I am having problem mounting my 2nd hdd and external hdd, it keeps giving error msg saying only root can do it.


rudy@rudy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a263a25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6549    52604810+   7  HPFS/NTFS
/dev/sda2            6550       57873   412254857+   5  Extended
/dev/sda3           57873       77826   160271360   83  Linux
/dev/sda5            6550       13076    52428096    7  HPFS/NTFS
/dev/sda6           13077       57873   359826729    7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8ace8ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77826   625130808+  42  SFS

Disk /dev/sdc: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0019b707

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465135104    7  HPFS/NTFS
rudy@rudy-desktop:~$ mount /dev /dscl


I am having problem with sdb1 (SFS file system ?) and sdc1 (external hdd)

please help

---

### Post by chopinhauer on 2010-08-08
> **lyonesse9 said:**
> 
I am having problem mounting my 2nd hdd and external hdd, it keeps giving error msg saying only root can do it.


There are several ways to gain 'root' privileges. When you connect your external hard-drive it should be mounted automatically (a daemon running 'root' does that), otherwise you can mount it from your Bookmarks menu or File Manager (no authentication should be required, maybe just your own password).

To gain 'root' privileges in the console prepend your commands with the 'sudo' command. Again your user password will be asked.

---


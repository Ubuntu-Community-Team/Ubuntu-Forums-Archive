---
title: "Grub boot menu is missing"
date: 2010-10-03
forum: General Help
---

### Post by diebodie on 2010-10-03
I recently decided to install ubuntu (10.4) on my secondary computer along side with the pre-installed windows vista. After installing Ubuntu  successfully I notice there was no boot menu and vista loaded by default. I re-booted hitting f10 to get to the boot menu where I finally found good old grub waiting. After toying with ubuntu a little and installing a few updates, I noticed the boot menu (grub) was gone altogether. I can no longer get into Ubuntu. I looked online for details but the whole tings sounds pretty sketchy. Anyone mind helping me walk-though this? 

I booted into the live CD and then I : > ubuntu@ubuntu:~$ sudo fdisk -lu

> 
I got this as the output [QUOTE]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d826b35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22956031    11476992    c  W95 FAT32 (LBA)
/dev/sda2   *    22956885   625137344   301090230    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7df736d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdd: 1994 MB, 1994273280 bytes
32 heads, 63 sectors/track, 1932 cylinders, total 3895065 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51f15b92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63     3894911     1947424+   6  FAT16




I believe my Ubuntu partition is the last one (around 20GB). What's next?

---

### Post by yetiman64 on 2010-10-03
All your partitions are showing up as FAT16, FAT32 or HPFS/NTFS (all Windows partitions). There are no "ext" partitions showing at all for Ubuntu.
Are you sure you didn't install Ubuntu using the wubi installer ? (Big difference to side by side partition installing.)

---

### Post by diebodie on 2010-10-03
> **yetiman64 said:**
> All your partitions are showing up as FAT16, FAT32 or HPFS/NTFS (all Windows partitions). There are no "ext" partitions showing at all for Ubuntu.
Are you sure you didn't install Ubuntu using the wubi installer ? (Big difference to side by side partition installing.)

*taking a look at the links*


I installed Ubuntu by booting into the live cd, resizing C: (without deleting any data) and installing it on the 20GB space I created. Thats side by side right?

---

### Post by yetiman64 on 2010-10-03
> **diebodie said:**
> *taking a look at the links*


I installed Ubuntu by booting into the live cd, resizing C: (without deleting any data) and installing it on the 20GB space I created. Thats side by side right?
Yes that sounds all right, maybe if you check link #1 in my sig and post the results back here in code tags may be a good place to start (the boot info script).

---


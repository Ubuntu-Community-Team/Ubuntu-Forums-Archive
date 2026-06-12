---
title: "My NTFS partition is gone and sda isn't big enough to contain it and there's no sdb"
date: 2010-08-28
forum: General Help
---

### Post by Colin Keenan on 2010-08-28
Ubuntu 10.04 (lucid)
Gnome 2.30.2
Kernel 2.6.32-24-generic
GCC Version 4.4.3 (i486-linux-gnu)
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
Total Memory 1886 MiB
NVIDIA GeForce 7050 PV / nForce 630a
NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010

When I did a clean install of Ubuntu 10.04 from CD several months ago, I told it to use the whole disk (removing the Windows 7 OS), but it automatically created a NTFS partition that was always mounted automatically and showed up as a file system called "Information" on my "Places" drop down menu.  My linux partitions were about 250 GB and the NTFS partition was over 300GB but I don't remember the exact size.  I used the "Information" file system frequently for backups and used it within the past couple of weeks.  Now "Information" no longer shows up in the "Places" drop down menu.  The problem may have started after a recent upgrade.  Below is what fdisk -l shows:

sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c12c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29697   238539776   83  Linux
/dev/sda2           29698       30402     5656577    5  Extended
/dev/sda5           29698       30402     5656576   82  Linux swap / Solaris

I don't know what device the NTFS "Information" file system used to be.

I installed GParted but it only shows device sda as 232.88 GiB and no other device.

I installed NTFS Configuration Tool, but it doesn't give me the option to enable internal NTFS.

I'm not really concerned about the backup information I had on that partition, but want to recover the storage space.

What should I do?

---

### Post by srs5694 on 2010-08-28
The disk whose information you've posted is 250 GB in size, and all of that size is allocated. Unless this "Information" partition was actually a virtual drive *inside* the existing partition, or unless you've deleted and resized it, it must have been on another physical disk (/dev/sdb, /dev/sdc, etc.; or possibly it was a network mount). Try showing us:


[list]
[*]The output of typing "cat /proc/scsi/scsi"
[*]The output of typing "ls -l /dev/[sh]d?"
[*]The output of typing "dmesg | grep sdb"
[*]The contents of /etc/fstab
[/list]


There may be clues in one or more of those items.

---


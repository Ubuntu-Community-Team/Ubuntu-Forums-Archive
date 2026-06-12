---
title: "Psychocats Mounting Procedure OK?"
date: 2010-11-17
forum: General Help
---

### Post by demonboy on 2010-11-17
Hello again,

Just following this guide to mounting Windows partition correctly [http://www.psychocats.net/ubuntu/mountwindowsfstab.]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

This is how I'm looking at the moment:

> 
jamie@jamie-NC10:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa0213ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        5408    37142031    7  HPFS/NTFS
/dev/sda3           10059       19458    75496448    7  HPFS/NTFS
/dev/sda4            5409       10059    37352449    5  Extended
/dev/sda5            5409        9862    35771392   83  Linux
/dev/sda6            9862       10059     1580032   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a34ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121598   976733184    7  HPFS/NTFS



1. Does this look ok?
2. Is it ok to follow the procedure on /dev/sda2 when this is my c:\ drive on my Windows XP boot?

---

### Post by wojox on 2010-11-17
Yes Aysiu is great at what he does.

---


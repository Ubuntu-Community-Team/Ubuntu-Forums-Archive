---
title: "How to mount my partitions ?"
date: 2011-04-21
forum: General Help
---

### Post by themacedonian on 2011-04-21
```
administrator@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25012501

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b61a7fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14592   117210208+   7  HPFS/NTFS
administrator@ubuntu:~$ 
```




I want to mount them permanently.
Thanks for help ..

---

### Post by bodhi.zazen on 2011-04-21
Add an entry in fstab =)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Mark Phelps on 2011-04-22
I see only NTFS partitions on your drives.  If this is the PC running Ubuntu, that means you installed it using Wubi -- and the Wubi filesystem is already resident on one of your NTFS partitions.

In Wubi, you typically access the Windows filesystem by looking at /host.

---


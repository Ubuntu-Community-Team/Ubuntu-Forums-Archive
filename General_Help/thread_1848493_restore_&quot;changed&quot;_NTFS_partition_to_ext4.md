---
title: "restore &quot;changed&quot; NTFS partition to ext4 with Disk Utils"
date: 2011-09-22
forum: General Help
---

### Post by noel4God on 2011-09-22
Hello! Thank you for trying to help me!

I did it! Edited the partition type with Ubuntu's Disk Utils:
           -> selected Linux (0x83) from HPFS/NTFS (0x07). On restart, couldn't mount it (/dev/sda5). Edited back to NTFS, nothing.
testdisk sais MFT (master file table) and MFT mirror are damaged.

??? Is there any way to reverse what I did with Disk Utils? Do you know any Linux data-recovery tools?

```
noel@noel-SN12E200:~$ sudo fdisk -l
[sudo] password for noel: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b19f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2624    20973856    7  HPFS/NTFS
/dev/sda3           23249       38914   125830296    7  HPFS/NTFS
/dev/sda4            2625       23248   165661545    f  W95 Ext'd (LBA)
/dev/sda5            7584       23248   125829112+   7  HPFS/NTFS
/dev/sda6            3016        7583    36690944   83  Linux
/dev/sda7            2625        3015     3139584   82  Linux swap / Solaris

```

Thank you for answering!
Noel

---

### Post by patryk77 on 2011-09-22
You should give testdisk a try. See this thread:

[http://ubuntuforums.org/showthread.php?t=1848068](http://ubuntuforums.org/showthread.php?t=1848068)

---


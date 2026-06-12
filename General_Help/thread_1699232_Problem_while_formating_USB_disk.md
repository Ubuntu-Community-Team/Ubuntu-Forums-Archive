---
title: "Problem while formating USB disk"
date: 2011-03-03
forum: General Help
---

### Post by teddytornado on 2011-03-03
Hi all,


I have created a new partition with fdisk.


Afterwards the output looks like follow:

fdisk -l /dev/sdb1 

```

Disk /dev/sdb1: 500.1 GB, 500073234432 bytes
255 heads, 63 sectors/track, 60797 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c965d38

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1       60798   488352736+   5  Extended

```Then I have formated the disk without any problems
mkfs -t ext3 /dev/sdb1

When I start fdisk -l /dev/sdb1 again the output is as follow. 
```

Disk /dev/sdb1: 500.1 GB, 500073234432 bytes
255 heads, 63 sectors/track, 60797 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb1 doesn't contain a valid partition table

```What is going wrong ? Where is the partition table ?

Many thanks,
Kai

---


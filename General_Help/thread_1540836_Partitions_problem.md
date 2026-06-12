---
title: "Partitions problem"
date: 2010-07-28
forum: General Help
---

### Post by Vishnu V on 2010-07-28
Hi
 I tried to recover deleted data using testdisk tool and now my partition table have some errors. Even though i have 3 partitions and 1 unallocated disk fdisk -l shows only 1 partition
```

vishnu@vishnu-laptop:~$ sudo fdisk -l
[sudo] password for vishnu: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  GPT

```
but i can view all partitions without any error in gparted. Please help me to fix this
Thanks

---

### Post by prodigy_ on 2010-07-28
Fix what? It just says that fdisk doesn't support GPT. Use ```
sudo parted -l
``` command instead.

---

### Post by Vishnu V on 2010-07-31
When i tried to install windows it says that GPT is not supported 
That was my problem and i formated the entire disk to install windows

---


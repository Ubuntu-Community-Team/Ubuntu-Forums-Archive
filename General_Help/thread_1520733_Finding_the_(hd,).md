---
title: "Finding the (hd?,?)"
date: 2010-06-29
forum: General Help
---

### Post by redcodefinal on 2010-06-29
Hey,
How do I check what the (hd?,?) is of a drive. I need it to properly set up grub. Any help is greatly appreciated.

---

### Post by Serpher on 2010-06-29
How many hardrives if you have? If only one the first '?' is a '0'. The second '?' is the partition number. Run:

```
fdisk -l /dev/sda
```

sda1-4 = Primary partition and anything above 5 is a logical partition. Basically just subtract 1 from the partition numbers you want and that's your partition number for the second '?'.

---

### Post by redcodefinal on 2010-06-29
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf29521d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23781   191020851   83  Linux
/dev/sda2           23782       24792     8120857+   5  Extended
/dev/sda5           23782       24792     8120826   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f0422

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3b8e3b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3863    31029516    7  HPFS/NTFS
/dev/sdb2            3864       36483   262020150    f  W95 Ext'd (LBA)
/dev/sdb5            3864       36483   262020118+   7  HPFS/NTFS

```
Sorry in my rush to get things done....

---

### Post by redcodefinal on 2010-06-29
> **Serpher said:**
> How many hardrives if you have? If only one the first '?' is a '0'. The second '?' is the partition number. Run:

```
fdisk -l /dev/sda
```sda1-4 = Primary partition and anything above 5 is a logical partition. Basically just subtract 1 from the partition numbers you want and that's your partition number for the second '?'.
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdf29521d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23781   191020851   83  Linux
/dev/sda2           23782       24792     8120857+   5  Extended
/dev/sda5           23782       24792     8120826   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f0422

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3b8e3b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3863    31029516    7  HPFS/NTFS
/dev/sdb2            3864       36483   262020150    f  W95 Ext'd (LBA)
/dev/sdb5            3864       36483   262020118+   7  HPFS/NTFS

```

---

### Post by Serpher on 2010-06-29
You're looking for:

**hd(0,0)**

---


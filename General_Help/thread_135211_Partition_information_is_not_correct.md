---
title: "Partition information is not correct"
date: 2006-02-23
forum: General Help
---

### Post by Eternal Blade on 2006-02-23
When I do a parition search using the command

```

fdisk -l

```

I get:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9483    76172166   83  Linux
/dev/sda2            9484        9726     1951897+  82  Linux swap / Solaris

```
Which is correct.  But then when I do:
```
di
```
I get:
```

Filesystem         Mount               Megs     Used    Avail %used fs Type
/dev/sda1          /                16732.8   2665.9  13217.0  21%  ext3
tmpfs              /dev/shm          1014.1      0.0   1014.1   0%  tmpfs
tmpfs              /lib/modules/2.   1014.1     12.3   1001.8   1%  tmpfs

```
How did I go from 80 gb to 18 gb?
To make matters worse if I run this command:
```
disktype /dev/sda
```
I get:
```

Block device, size 74.51 GiB (80000000000 bytes)
GRUB boot code, compat version 3.2, boot drive 0xff
DOS partition map
Partition 1: 72.64 GiB (78000297984 bytes, 152344332 sectors from 63)
  Type 0x83 (Linux)
  FAT16 file system (hints score 4 of 5)
    Volume size 54.75 MiB (57413632 bytes, 28034 clusters of 2 KiB)
    Volume name "DellUtility"
  Ext3 file system
    Volume name "/"
    UUID 9D24F578-1188-4F74-8E20-D8CF838DB64A (DCE, v4)
    Volume size 16.60 GiB (17825792000 bytes, 4352000 blocks of 4 KiB)
Partition 2: 1.861 GiB (1998743040 bytes, 3903795 sectors from 152344395)
  Type 0x82 (Linux swap / Solaris)
  Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
    Swap size 1.861 GiB (1998733312 bytes, 487972 pages of 4 KiB)

```
Which makes even less sense since it tells me that there is about 80 gb on that partition, but only shows about 17 gb.

My question is, where did my 60 gb go or what can I do to find this out?

---

### Post by lamego on 2006-02-23
Have you tried a file system chek on it ? (fsck)
I don't know if this can be done on linux, on comercial unixes with LVM it is possible to create a filesystem which just uses a piece of the partitition.
Have you installed with LVM support for the partitioning ?

---


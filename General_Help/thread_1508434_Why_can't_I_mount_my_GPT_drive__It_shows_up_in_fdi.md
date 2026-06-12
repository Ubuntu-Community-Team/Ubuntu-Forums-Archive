---
title: "Why can't I mount my GPT drive?  It shows up in fdisk..."
date: 2010-06-12
forum: General Help
---

### Post by sofakng on 2010-06-12
I'm using Hyper-V and using physical disk pass-through to pass a physical disk to Ubuntu but I'm having problems.

Here's my fdisk -l output:
```

Disk /dev/sdb: 2199.0 GB, 2199023255552 bytes
256 heads, 63 sectors/track, 266305 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT
```

However, the special device **/dev/sdb1** doesn't exist so I can't mount it.

Is this normal for GPT drives?  Am I doing something wrong?

---

### Post by sanderj on 2010-06-13
What have you tried to mount the partition? And what was the result?

And: is this the full 'sudo fdisk -l' output?

---

### Post by srs5694 on 2010-06-13
The Linux fdisk utility only shows the protective MBR, which is a data structure designed to protect GPT disks from damage by GPT-unaware tools. The *real* partitions on the disk can't be identified by fdisk; you'll need to use [GPT fdisk (aka gdisk),](http://www.rodsbooks.com/gdisk/) an fdisk-like tool; or a libparted-based program, such as the text-based GNU Parted or the GUI GParted.

If /dev/sdb1 doesn't exist, then chances are that either the disk has a GUID Partition Table defined but it contains no partitions, or that the first partition on the disk has a number other than 1. (This is perfectly legal, in both MBR and GPT.) Either look at the disk with gdisk, parted, or some other GPT-aware tool, or type "ls /dev/sdb*" to see all the partitions that the kernel recognizes.

---


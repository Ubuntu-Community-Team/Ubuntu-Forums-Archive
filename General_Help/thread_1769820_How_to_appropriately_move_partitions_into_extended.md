---
title: "How to appropriately move partitions into extended partition?"
date: 2011-05-28
forum: General Help
---

### Post by l07 on 2011-05-28
I'd like to create a swap partition having already reached the four partitions per disk limit. So I'd like to create an extended partition and move some partitions into it. The question is which partitions to move and where to create the extended partition.

Some partitions have so much data that I cannot back them up, so I'd  prefer to avoid performing operations that might risk them. 

By the way,  is there a command line tool that provides equivalent output as gparted?

---

### Post by srs5694 on 2011-05-28
Fortunately, you've got gaps between your partitions, so you can convert any or all of them into logical partitions using my [FixParts](http://www.rodsbooks.com/gdisk/fixparts) program. Its Web page describes its use. That Web page also describes creating a backup of your partition table, which will be vitally important if something goes badly wrong, so be sure to create that backup. I'd convert the last two or three partitions into logicals, then resize whatever's least important (because of the risks) to make room for a swap partition.

Alternatively, since you're not using the disk for Windows, you could convert it to use the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning system, which doesn't distinguish between primary, extended, and logical partitions. You can do this with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program. If you do this, though, it will be a practical necessity to create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) (gdisk type code EF02 or set the "bios_grub flag" on a new partition with GParted -- do *not* turn any existing partition into a BIOS Boot Partition!). You'll also have to re-install GRUB, which *probably* won't be necessary if you use FixParts to convert one or more primaries into logicals. Thus, the GPT route does involve more immediate up-front effort, but it might be simpler down the road, should some other adjustment run into primary/extended/logical issues.

An alternative to either type of conversion is to create a swap *file* rather than a swap *partition*. This would require no changes to your partitions; just create an empty file in whatever partition has space to spare, use mkswap on it, and add it to /etc/fstab. There's almost certainly a Web page that describes the process in more detail, but I don't have a reference; try a Web search.

---

### Post by l07 on 2011-05-29
I decided to just use a swap file. I may later convert to GPT. Thanks for your help.

---


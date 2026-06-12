---
title: "Copying from/to partition extremly slow"
date: 2010-03-19
forum: General Help
---

### Post by Gegenzeit on 2010-03-19
Hello,

When I copy to/from my data partition I only get 1.1 Mib/s - and I have no idea why. I first thought this was a problem with my USB-settings (or devices), but then realized that it does also happen when I copy from partition to partition. The problem is definetely connected to /sda8.

My partitions:

sda1: Windows, nfts
sda3: Games and Data, nfts
sda2: extended Partition, ext4
.......sda6: Linux system partition, ext4
.......**sda8: Data, ext4 ---> THIS IS THE PARTITION WHICH IS TOO SLOW!**
.......sda9: currently not in use, ext4
.......sda7: Linux-swap
.......unallocated
.......sda5: Recovery, fat32

Anyone any idea?

Thanks

Jörg

---

### Post by srs5694 on 2010-03-19
This is a long shot, but: What sort of hard disk is it? If it's a new (December 2009 or later) Western Digital Caviar Green drive, this may be a problem with the alignment of the partitions. If a partition doesn't begin on a 4096-byte boundary, performance can be severely degraded, particularly when writing many small files.

---


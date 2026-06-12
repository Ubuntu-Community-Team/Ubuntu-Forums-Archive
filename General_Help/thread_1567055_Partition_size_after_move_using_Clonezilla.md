---
title: "Partition size after move using Clonezilla"
date: 2010-09-03
forum: General Help
---

### Post by bateybates on 2010-09-03
I used Clonezilla to image a Ubuntu partition of 18GB and restored it to a partition of 30GB. (showing as "sdb1")

I understand now that I should have put it onto a partition the same size as the original and then resized that partition with Gparted, but I put it directly onto a larger partition and thought all was well, but now I'm running into disk space warning messages.

It still works fine but the OS still seems to think it is still on an 18GB partition and that it is running out of space.

The partition "sdb1",  is on a large drive I partitioned with Gparted.

The various utils I have to look at partitions do not agree:

*Disk Utility reports sdb1 size as 33GB
*KDE Partition Manager reports sdb1 size as 30.28GB with 15.59GB used (therefore 14.69GB free)
*KDiskFree reports sdb1 size as 18.3GB with 1.8GB free
*Gparted reports sdb1 size as 30.28GB with 27.54GB used
*Gparted (used after booting from a Mint installation) give same result
*PROPERTIES (using live knoppix DVD) shows size of files as 16.0GB (16.5GB on disk)

After booting with Knoppix DVD and trying to copy everything onto another drive (to see how many GB there are) gives "invalid or incomplete multibyte or wide character" error message.

I'd be grateful if someone could tell me how to sort this out, without resizing the partition as I've got a lot of data on the HD now.

---

### Post by bateybates on 2010-09-05
I found the answer in this thread:
[http://ubuntuforums.org/showthread.php?t=1432008](http://ubuntuforums.org/showthread.php?t=1432008)

I had to run sudo resize2fs /dev/sdd1 

and that took a few minutes to fix the problem.

---


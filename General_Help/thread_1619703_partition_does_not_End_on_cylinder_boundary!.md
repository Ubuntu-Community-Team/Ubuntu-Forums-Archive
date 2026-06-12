---
title: "partition does not End on cylinder boundary!"
date: 2010-11-12
forum: General Help
---

### Post by Konbuntu on 2010-11-12
i was looking at the list of my /dev/sda partition and on the first partition it says that it does not end on cylinder boundary...

does is it need to be fixed?
 on a book that im reading it says that when you create a partition the end cylinder should be the size of the partition...

:confused:

---

### Post by ajgreeny on 2010-11-12
I don't think it is of any consequence any more, though it used to be.  Something to do with partitioning and partition tables which have now moved on beyond such problems.

I have not seen this for some time as I always make partitions manually before installing ubuntu using gparted, and the default for that I think is to set partitions to cylinder boundaries.  But as I say, it does not matter any more so you can ignore it, perhaps until you install next time.

---

### Post by Konbuntu on 2010-11-12
good =)

thanks!

---

### Post by srs5694 on 2010-11-12
Ajgreeny is correct. To elaborate, in the PC stone age, disks were addressed using cylinder/head/sector (CHS) values, and partitions were conventionally started on cylinder boundaries to improve performance. Some very old OSes, such as some versions of DOS, assume that disks will be partitioned in this way, and may misbehave if partitions don't begin and end at appropriate points.

By the mid-1990s, if not earlier, CHS values had become a fiction; disks had different true physical CHS values than they reported to the BIOS. Performance issues related to cylinder alignment faded into nothingness, too. By the mid-to-late 1990s, BIOSes and disks were beginning to use Logical Block Addressing (LBA) mode rather than CHS mode; in LBA mode, CHS values aren't used at all, and instead a single number is used to identify each partition. Nonetheless, partitioning software continued to use cylinder alignment, partly out of habit and partly to satisfy the needs of DOS and other old tools.

With the advent of LBA mode, the CHS data in the Master Boot Record (MBR) partitioning system used on most disks became largely useless, and aligning partitions on cylinder boundaries became completely pointless. Other factors have become important, such as performance issues with certain types of RAID arrays, SSD technologies, and the new [Advanced Format disks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) These issues typically favor aligning partitions on boundaries of 4 KiB or multiples thereof, often up to about 256 KiB, or occasionally higher. These values seldom correspond to cylinder boundaries. Thus, starting with Windows Vista, Microsoft began aligning partitions on 1 MiB boundaries, and other tools, including the latest generation of Linux tools, is favoring similar partition alignment policies.

Older tools will sometimes complain about such alignment, but it does no harm unless you're using *very* old software, such as DOS or extremely old partitioning software that refuses to work correctly expect with cylinder-aligned partitions.

---

### Post by mister_playboy on 2010-11-12
> **srs5694 said:**
> Ajgreeny is correct. To elaborate, in the PC stone age, disks were addressed using cylinder/head/sector (CHS) values, and partitions were conventionally started on cylinder boundaries to improve performance. Some very old OSes, such as some versions of DOS, assume that disks will be partitioned in this way, and may misbehave if partitions don't begin and end at appropriate points.

By the mid-1990s, if not earlier, CHS values had become a fiction; disks had different true physical CHS values than they reported to the BIOS. Performance issues related to cylinder alignment faded into nothingness, too. By the mid-to-late 1990s, BIOSes and disks were beginning to use Logical Block Addressing (LBA) mode rather than CHS mode; in LBA mode, CHS values aren't used at all, and instead a single number is used to identify each partition. Nonetheless, partitioning software continued to use cylinder alignment, partly out of habit and partly to satisfy the needs of DOS and other old tools.

With the advent of LBA mode, the CHS data in the Master Boot Record (MBR) partitioning system used on most disks became largely useless, and aligning partitions on cylinder boundaries became completely pointless. Other factors have become important, such as performance issues with certain types of RAID arrays, SSD technologies, and the new [Advanced Format disks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) These issues typically favor aligning partitions on boundaries of 4 KiB or multiples thereof, often up to about 256 KiB, or occasionally higher. These values seldom correspond to cylinder boundaries. Thus, starting with Windows Vista, Microsoft began aligning partitions on 1 MiB boundaries, and other tools, including the latest generation of Linux tools, is favoring similar partition alignment policies.

Older tools will sometimes complain about such alignment, but it does no harm unless you're using *very* old software, such as DOS or extremely old partitioning software that refuses to work correctly expect with cylinder-aligned partitions.

Thanks for sharing... seems to be a case of "old habits die hard". :popcorn:

---


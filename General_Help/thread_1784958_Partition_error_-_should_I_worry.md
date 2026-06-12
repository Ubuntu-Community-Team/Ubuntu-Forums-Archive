---
title: "Partition error - should I worry"
date: 2011-06-17
forum: General Help
---

### Post by ianc1 on 2011-06-17
Hi everyone

I used fdsik the other night to determine a partition number and I noted that my install which did the partitioning seems to have created an error.

Output of fdisk -l```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         426     3417088   83  Linux
Partition 1 does not end on cylinder boundary.
```Output of fdisk -lu```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011e69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     6836223     3417088   83  Linux
Partition 1 does not end on cylinder boundary.
```Should I worry about this error?  Even if I shouldn't I'd like to know what I did wrong and how to resolve it.

Does anyone have any clues?  Thanks

---

### Post by ajgreeny on 2011-06-17
If you are worried about the "Partition 1 does not end on cylinder boundary." comment, you can forget about that, it is of no importance any more, and has not been for some years.

It is a relic from the days of much smaller hard disks with different physical and file system properties, but is of absolutely no consequence any more.

---

### Post by ianc1 on 2011-06-17
Many thanks, I'm glad I don't need to do another install.  I assume its because the partition does not end at a particular cylinder/head.  Is this something that others encounter on installs using the live USB install method?

I'd still like to know how to avoid/resolve it.  Do you have any ideas/suggestions so that I avoid this error, albeit an unimportant one?

Thanks

---

### Post by ajgreeny on 2011-06-18
It's an error that appears on these forums quite a lot, or has done in the past.

If it really worries you it is possible to use gparted in advance of installing to make your partitions, and set that to use cylinder boundaries,  see my screenshot

---

### Post by ianc1 on 2011-06-18
Thanks again for your help, looking at gparted it seems to be pretty obvious as your image indicated.  I assume if doing this before a fresh install I should use Gparted on a live USB or similar live media rather than from within the working pc if it is the one to be upgraded.

---

### Post by wildmanne39 on 2011-06-18
> **ianc1 said:**
> Thanks again for your help, looking at gparted it seems to be pretty obvious as your image indicated.  I assume if doing this before a fresh install I should use Gparted on a live USB or similar live media rather than from within the working pc if it is the one to be upgraded.Hi, yes from the livecd.

---

### Post by oldfred on 2011-06-19
as ajgreeny originally suggested. Cylinders have not been used by drives since drives became larger than 8GB. Back then when installing a drive we had to plug in heads, sectors, & cylinders. When that exceeded what the BIOS could store they converted to LBA - large block allocation.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

Now they are installing partitions on different boundaries for better compatibly with SSD and 4K drives.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by ianc1 on 2011-06-22
Thanks oldfred, an excellent set of links which have provided me with lots of info and a better understanding of this.  Thanks again.

---


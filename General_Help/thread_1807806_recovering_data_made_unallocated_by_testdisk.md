---
title: "recovering data made unallocated by testdisk"
date: 2011-07-19
forum: General Help
---

### Post by danieltl on 2011-07-19
I was trying to recover data from a HD that had XP on it but became unbootable, I suspect due to corrupt boot sector. I downloaded Ubuntu 11.04 and burned to CD.

At first, fdisk -l command produced a list of partitions which included the largest one (232 GB) with data on it (sda2) as well as what is suspected to be my Windows boot partition (sda5). Unfortunately, I was unable to mount the partitions, getting various error messages, so I tried to use "testdisk." After "recovering" two partitions, I cannot locate the 232 GB partition. fdisk only shows 3 small partitions. In GParted, the 232 GB partition is now listed as "unallocated." I still haven't rebooted after the testdisk write, for fear that I may lose (or may have lost) all my data. 

Any ideas? I've searched without luck for solutions.


thanks.

---


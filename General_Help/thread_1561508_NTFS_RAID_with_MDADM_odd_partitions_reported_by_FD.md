---
title: "NTFS RAID with MDADM: odd partitions reported by FDISK"
date: 2010-08-26
forum: General Help
---

### Post by skulls on 2010-08-26
Hi,

This problem is recurrent and reproducible, it has happened to other users who have reported it but so far haven't had an answer. The problem happens when you create a RAID array (no matter what type) with MDADM, and it is then formatted to NTFS with mkfs or similar. 

For reference, I want to create a RAID1 volume with two 1TB drives formatted as NTFS, everything works as expected but the output of fdisk -l is as follows:

```

Disk /dev/md0: 1000.2 GB, 1000202101760 bytes
2 heads, 4 sectors/track, 244189966 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/md0p1 ? 822447 240553456 958924038+ 70 DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/md0p2 ? 244156454 471478443 909287957+ 43 Unknown
Partition 2 does not end on cylinder boundary.
/dev/md0p3 ? 28216909 28216910 5 72 Unknown
Partition 3 does not end on cylinder boundary.
/dev/md0p4 330301441 330307927 25945 0 Empty
Partition 4 does not end on cylinder boundary.
```


The output from palimpsest is similar. 

As you can see, it would appear that something is wrong with the ntfs. However ntfsfix doesn't complain and I have done several consistency checks, none of which has failed. I am confused and furthermore afraid that I might corrupt the data. 

Can someone please clarify whether this is a serious issue or just a confusing bug?

---

### Post by srs5694 on 2010-08-26
You're trying to interpret the contents of a filesystem as if it were a partition table. A software RAID array is *created from* individual partitions, but does not itself *contain* partitions, at least not as you've configured it -- it contains a filesystem.

Also, why would you put NTFS on a *Linux* software RAID array? AFAIK, Windows can't access it, so using NTFS on it is asking for trouble -- as soon as there's a power failure or other minor problem, it will be impossible to correct it, since Linux lacks good NTFS maintenance tools. Use a Linux filesystem, not NTFS, on this array.

---

### Post by skulls on 2010-08-27
Thanks for the quick reply! See my answer on the other RAID-related post [here]("http://ubuntuforums.org/showpost.php?p=9772382&postcount=4")

---


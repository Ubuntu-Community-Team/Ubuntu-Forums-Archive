---
title: "Major problem in formatting drives (applies to all versions of UBUNTU)"
date: 2010-05-06
forum: General Help
---

### Post by deadeye1989 on 2010-05-06
Hi,
i am complaining about a problem of aligning the ext3 and ext4 partition which causes lot of slowness to my ubuntu :((((.
the problem can be fixed in windows by installing WD advanced format utility or acronis aligning for partition.
the MAJOR DRAWBACK is that the acronis aligning don't support the linux with all it's drives !!!!.
please if you know any utility in ubuntu instead of acronis aligning please tell me !


best regards..,
Mohammed Nasr

---

### Post by srs5694 on 2010-05-06
You only need to worry about partition alignment if you're using a disk with 4096-byte sectors (currently just Western Digital Advanced Format drives) or certain types of hardware RAID arrays.

If you've got such a disk and have *not* already partitioned it, you can read [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) that I wrote recently for IBM developerWorks with advice on how to deal with the disk. This article is geared towards users with disks that aren't already partitioned, though.

If you've got such a disk and you *have* already partitioned it, then it'll be tougher to deal with. You could conceivably move/resize your partitions using GNU Parted or GParted, but you'll need to be very careful to get the partition start points right. You should use the very latest version of Parted/GParted available, even if it means you've got to compile it from source code. Another option would be to back up, repartition correctly, and restore; or shrink your current partitions, create new ones that are properly aligned, and copy your data to the new partitions.

If you could post the output of a "sudo fdisk -l" command and point out which is the affected disk, I might be able to offer more specific suggestions. (Please post the output between [noparse]```

```[/noparse] tags for increased legibility.)

---


---
title: "flash drive problems"
date: 2009-07-17
forum: General Help
---

### Post by cong06 on 2009-07-17
Yesterday I got a "super block" error. The number was wrong, or something. I wish I had saved it, but I assumed it was a problem with my flash drive.
So I wipped it and reformatted this one ntfs.

Then I got home and my other flash drive had the same problem. (so two different Jaunty machines started recognizing two different flash drives as corrupt. both fat32) In a rush to fix the problem I wiped that one too and gave it ext3 because that's what fdisk defaulted to (gparted was hanging, and would never finish the initial scan).

At this point I noticed that Ubuntu (3 different Jaunty machines) stopped mounting the flash drives automatically (one ntfs, one ext3). No reason, I simply had to sudo mount, to get the flash drive accessible.

This morning when I try to use the newly wiped flash drive with 8 GB of music, I realize it only has 900MB of music, and the partitions are all screwed up:
```

The number of cylinders for this disk is set to 1965.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdc1: 16.1 GB, 16170868224 bytes
255 heads, 63 sectors/track, 1965 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/sdc1p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc1p3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc1p4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---


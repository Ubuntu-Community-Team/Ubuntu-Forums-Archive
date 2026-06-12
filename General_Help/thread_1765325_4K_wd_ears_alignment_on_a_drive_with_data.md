---
title: "4K wd ears alignment on a drive with data"
date: 2011-05-22
forum: General Help
---

### Post by covert on 2011-05-22
Hi. My system has been suffering from hi wa% in top and with my exploring of the problem I found it could be related to my miss-aligned WD EARS hd.

What tool can I use to re-align the partitions without destroying all the data or having to re0install the system ?

```
#sudo parted /dev/sda unit s print
Model: ATA WDC WD15EARS-00Z (scsi)
Disk /dev/sda: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      63s          29302559s    29302497s    primary   ext3            boot
 2      29302560s    2930272064s  2900969505s  extended
 5      29302623s    37110149s    7807527s     logical   linux-swap(v1)
 6      37110213s    37495709s    385497s      logical   ext3
 7      37495773s    1014054929s  976559157s   logical   jfs
 8      1014054993s  2930272064s  1916217072s  logical   jfs

```

---

### Post by srs5694 on 2011-05-23
In principle, GParted should be able to do it. You'll need to resize every primary and logical partition on the disk (the alignment of the extended partition is irrelevant), and set the "align to MiB" option. (This option appears in relatively new versions of GParted, but not in older ones.) I'm not sure if you'll need to explicitly shift the start points of your partitions or not. You might want to do it one partition at a time, verifying that the start points are correct after each adjustment, and start with the smaller ones so as to minimize the time investment and risk if you need to make a few attempts before you get it right.

Be aware that GParted sometimes fails to resize partitions when your alignment options don't match those of surrounding partitions; it complains that it couldn't satisfy all the constraints. I suspect this is because of a rounding issue causing the tool to try to set a size that overlaps a partition. This problem can usually be worked around by putting a small gap between the partition you're resizing and the surrounding partitions.

Finally, you should be very aware that resizing partitions is inherently risky. Back up your data before you try. Given this need and the fact that both the backup and the resize will be reading significant amounts of data from poorly-performing disks, you might want to back up, wipe clean, repartition correctly, and restore the data. That might be quicker than attempting to back up and resize all your partitions.

---


---
title: "Using testdisk to try to restore RAID1 HDD partition"
date: 2012-04-09
forum: General Help
---

### Post by kyleflan on 2012-04-09
I've been trying to mount a drive from an iOmega NAS (ix2-200) which was set up as part of a RAID1. I've tried mounting the drive manually, but I couldn't, and someone suggested testdisk. 

However, I'm not totally certain how to use testdisk and I don't want to lose the data on the drive. Here's what I've done so far.

testdisk -> Selected /dev/sdf2 -> Analyse ->

```
Disk /dev/sdf - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Linux                    0   0  2   253 254 63    4080509
No EXT2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                  254   0  1 121601  80 63 1949444658
 2 P Linux                  254   0  1 121601  80 63 1949444658
No partition is bootable

```

...-> Quick Search -> N (no to search Vista partitions) ->

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdf - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   0  2   253 254 63    4080509
D Linux RAID               0   0  2   253 254 63    4080509 [md0]
P Linux LVM              254   0  1 121601 254 63 1949455620

```

Here is where I'm lost as to what to do. The testdisk documentation describes recovering an NTFS disk and wasn't very clear here.

If I want to get the data from the drive, should I add the "Linux RAID" partition back, or just add the "Linux LVM" partition?

Thanks for the help!

---


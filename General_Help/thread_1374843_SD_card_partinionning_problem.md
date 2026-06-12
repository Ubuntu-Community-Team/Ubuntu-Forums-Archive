---
title: "SD card partinionning problem"
date: 2010-01-07
forum: General Help
---

### Post by grivet on 2010-01-07
Hi, 

I try to create partitions on a SD card. I would like to create first fat32 partition  of 100M and a second ext2 partition of the rest of the SD card size. I use GParted to do this job but it is not able to create the first Fat32 partition. I able to create the ext2 partition

This is the log file of GParted


GParted 0.4.8
 Libparted 1.8.8.git-dirty


    **Create Primary Partition #1 (fat32, 101.98 MiB) on /dev/mmcblk0**  00:00:02    ( ERROR )             create empty partition  00:00:01    ( SUCCESS )             [I]path: /dev/mmcblk0p1
start: 63
end: 208844
size: 208782 (101.94 MiB)[/I]          set partition type on /dev/mmcblk0p1  00:00:01    ( SUCCESS )             *new partition type: fat32*          create new fat32 file system  00:00:00    ( ERROR )             ***mkdosfs -F32 -v -n "" /dev/mmcblk0p1***             *sh: /usr/bin/nice: Input/output error*

---


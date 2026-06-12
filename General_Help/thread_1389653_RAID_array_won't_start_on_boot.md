---
title: "RAID array won't start on boot"
date: 2010-01-24
forum: General Help
---

### Post by jbouzane on 2010-01-24
I've been having this problem for some time; I don't remember when it started, but it was probably while upgrading the distro a few releases back.

I have two raid arrays configured in my raidtab, both raid1. When I boot the machine, one of them starts and the other does not. To get the other going, I have to manually add the disks to the array with mdadm:

sudo mdadm -A /dev/md0 /dev/sda2 /dev/sdb2

Then, the array is started and I can mount it normally. The other array mounts normally on boot.

I can't seem to figure out what the difference is between the two arrays. mdadm can't seem to find the array unless I tell it that it exists:

sudo mdadm --detail --scan
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c0c2835e:40492eb4:ed430286:e468258a

(Note that's the other array, md1, which it starts just fine).

Here's the output of mdadm --examine on the two partitions in the array:

sudo mdadm --examine /dev/sda2 /dev/sdb2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d63f1ebc:632c9c27:2cb1b813:e24db512
  Creation Time : Sun Oct  7 00:01:27 2007
     Raid Level : raid1
  Used Dev Size : 725246272 (691.65 GiB 742.65 GB)
     Array Size : 725246272 (691.65 GiB 742.65 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Jan 24 13:31:25 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : af364271 - correct
         Events : 0.5256


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d63f1ebc:632c9c27:2cb1b813:e24db512
  Creation Time : Sun Oct  7 00:01:27 2007
     Raid Level : raid1
  Used Dev Size : 725246272 (691.65 GiB 742.65 GB)
     Array Size : 725246272 (691.65 GiB 742.65 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Jan 24 13:31:25 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : af364283 - correct
         Events : 0.5256


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2

I see this line in dmesg about md1, but nothing about md0:

[   71.230095] raid1: raid set md1 active with 2 out of 2 mirrors

Here's my raidtab file:

raiddev /dev/md0
        raid-level      1
        nr-raid-disks   2
        nr-spare-disks  0
        persistent-superblock 1
        device          /dev/sda2
        raid-disk       0
        device          /dev/sdb2
        raid-disk       1

raiddev /dev/md1
        raid-level      1
        nr-raid-disks   2
        nr-spare-disks  0
        persistent-superblock 1
        device          /dev/sdc1
        raid-disk       0
        device          /dev/sdd1
        raid-disk       1

And finally, here are the partition tables for the two drives that won't mount:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         912     7325608+  83  Linux
/dev/sda2             913       91201   725246392+  fd  Linux raid autodetect
/dev/sdb1               1         912     7325608+  83  Linux
/dev/sdb2             913       91201   725246392+  fd  Linux raid autodetect

The two raid drives are correctly configured as raid autodetect partitions.

Does anyone have any ideas what's wrong here? My only guess is that the kernel can't autodetect a raid volume if it's not the first partition on the drive. Is anyone else doing this successfully? The kernel I'm running is:

uname -sr
Linux 2.6.24-26-server

Any help is greatly appreciated.

---


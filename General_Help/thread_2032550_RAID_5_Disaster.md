---
title: "RAID 5 Disaster"
date: 2012-07-24
forum: General Help
---

### Post by Diverdez on 2012-07-24
Hello,
I've been running Ubuntu 12.04 with 3 disks set up with raid 5.  The system crashed this morning (no idea why), and now only boots in recovery mode.  It looks like the system is fine with the swap partition that is raid'd, but the main partition is now reporting:

md/raid:md0: not enough operational devices (2/3 failed)
md/raid:md0: failed to run raid set.
md: pers->run() failed ...
mdadm: failed to start array /dev/md/0: Input/output error
mdadm: CREATE user root not found
mdadm: CREATE group disk not round
mdadm: /dev/md/0 is already in use.
Could not start the RAID in degraded mode.

Looking in /proc/mdstat I've got the following

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdc5[2] sda5[0] sdb5[1]
      8166400 blocks super 1.2 level5, 512k chunk, algorithm 2 [3/3] [UUU]

md0 : inactive sda1[3]
      1949426688 blocks super 1.2

unused devices: <none>



I've also run a mdadm --detail /dev/md0 and I get this:

    Raid Level : 5
  Raid Devices : 3
 Total Devices : 1
   Persistence : Superblock is persistent

    Update Time : Tue Jul 24 07:51:07 2012
          State : active, FAILED, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Ubuntu:0
           UUID : b0d30657:91630fe4:0a591a3e:37aef82d
         Events : 11099

Number Major Minor RaidDevice State
   3     8      1      0      active sycn   /dev/sda1
   1     0      0      1      removed
   2     0      0      2      removed


Disks 1 & 2 are working, cos they're fine for /dev/md1 and are all showing as active sync.

Is there anyway that I can restore /dev/md0 as a working array?  I'm pretty sure that the actual data on the disks is probably ok.  Or is the fact that I've "lost" 2 out of the 3 disks terminal as far as the array is concerned, and I'm going to have to reinstall and get the data back from backups?

I've had a problem in the past where I had 1 disk showing as removed, and I "fixed" that by zero-ing the superblock, and then adding it back in to the raid.  The disk then took a number of hours to re-sync.  I doubt that this will work with 2 of the 3 disks though.

Any advice would be gratefully received...

---


---
title: "spare not rebuilding?"
date: 2011-06-27
forum: General Help
---

### Post by DaveHowe on 2011-06-27
Hi All,

  Had a couple of goes at this, decided it might be smarter to ask around a bit before I do anything drastic.

  Had some recent issues with a server - 9.10, running in a hosting center (so I have no direct hardware access).

smartmon showed some issues, so I triggered a short test - and the drive bugged out, taking down the whole server (which worried me a bit as this is supposed to be raid 1)

rebooting saw only one of the two drives, and the main data partition was at state "spare" and was not available for service in degraded state.

hardware reset brought the original back to life, so I checked and it was in the rebuilding state:



```
/dev/md2:
        Version : 00.90
  Creation Time : Wed Feb 17 00:03:20 2010
     Raid Level : raid1
     Array Size : 1458830400 (1391.25 GiB 1493.84 GB)
  Used Dev Size : 1458830400 (1391.25 GiB 1493.84 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Jun 27 17:25:19 2011
          State : active, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           UUID : e5e65dac:b388bfd1:776c2c25:004bd7b2
         Events : 0.2946605

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       2       8       19        1      spare rebuilding   /dev/sdb3

========================
/dev/sda3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e5e65dac:b388bfd1:776c2c25:004bd7b2
  Creation Time : Wed Feb 17 00:03:20 2010
     Raid Level : raid1
  Used Dev Size : 1458830400 (1391.25 GiB 1493.84 GB)
     Array Size : 1458830400 (1391.25 GiB 1493.84 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2

    Update Time : Mon Jun 27 17:25:19 2011
          State : active
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : aaf72889 - correct
         Events : 2946605


      Number   Major   Minor   RaidDevice State
this     0       8        3        0      active sync   /dev/sda3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       0        0        1      faulty removed
   2     2       8       19        2      spare   /dev/sdb3
========================

/dev/sdb3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e5e65dac:b388bfd1:776c2c25:004bd7b2
  Creation Time : Wed Feb 17 00:03:20 2010
     Raid Level : raid1
  Used Dev Size : 1458830400 (1391.25 GiB 1493.84 GB)
     Array Size : 1458830400 (1391.25 GiB 1493.84 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2

    Update Time : Mon Jun 27 17:25:19 2011
          State : active
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : aaf72897 - correct
         Events : 2946605


      Number   Major   Minor   RaidDevice State
this     2       8       19        2      spare   /dev/sdb3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       0        0        1      faulty removed
   2     2       8       19        2      spare   /dev/sdb3
========================

Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] [linear] [multipath]
md2 : active raid1 sdb3[2] sda3[0]
      1458830400 blocks [2/1] [U_]

md1 : active raid1 sda2[0] sdb2[1]
      2104448 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      4200896 blocks [2/2] [UU]

unused devices: <none>




```

Now, when I first started this, it began to rebuild the spare - fairly slowly, but ETA was about 15 hours which I could live with.  however, after about 6% of the rebuild, the rebuild counter in /proc/mdstat vanished and mdadm -monitor logged the rebuild as complete, which clearly it wasn't.

Any clues? Trying not to have this box down too long (as it is a live server) but here are things I thought of trying:

1) fsck on /dev/md2 from rescue cd then re-attempt rebuild

2) dd /dev/sda3 --> /dev/sdb3

3) fail and remove sdb3; build a new array (with one prefailed) on sdb3, mount both it and md2 (via rescue cd) and cp -r md2->new volume

I have taken offsite backups, but would rather not have to rebuild this machine from scratch to restore them... any suggestions or thoughts on my plans above?

---


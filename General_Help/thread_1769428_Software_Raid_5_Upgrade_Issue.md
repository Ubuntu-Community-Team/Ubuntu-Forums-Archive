---
title: "Software Raid 5 Upgrade Issue"
date: 2011-05-28
forum: General Help
---

### Post by dizzident on 2011-05-28
So I upgraded from 10.04->->11.04 and in the process the super blocks of a few of my raid drives went missing. So I did what I normally did before and recreated the raid.

sudo mdadm --create /dev/md0 --verbose --assume-clean --level=5 --raid-devices 9 /dev/sdc /dev/sde /dev/sdf /dev/sda /dev/sdd /dev/sdj /dev/sdi /dev/sdh /dev/sdg -c 256

My folly was not realizing the meta data had changed from 0.90 to 1.2. I stopped the raid and rebuilt it with meta-data 0.90 but now it's saying the file system is corrupt because I'm missing space.

An examine before the rebuild: 
          Magic : a92b4efc
        Version : 0.90.00
           UUID : b2a88a65:84a19068:1feaa8f8:e87b7f75
  Creation Time : Fri Oct 22 18:10:39 2010
     Raid Level : raid5
  Used Dev Size : 1465138432 (1397.26 GiB 1500.30 GB)
     Array Size : 11721107456 (11178.12 GiB 12002.41 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0

    Update Time : Fri May 27 21:46:14 2011
          State : clean
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0
       Checksum : daf351bc - correct
         Events : 954146

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       48        4      active sync   /dev/sdd
   5     5       8      160        5      active sync
   6     6       8      144        6      active sync   /dev/sdj
   7     7       8      128        7      active sync   /dev/sdi
   8     8       8       16        8      active sync   /dev/sdb

An examine after the rebuild:
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : afb6e3e0:a19907d2:da6b9838:6b06fb97 
  Creation Time : Sat May 28 00:00:24 2011
     Raid Level : raid5
  Used Dev Size : 1465137408 (1397.26 GiB 1500.30 GB)
     Array Size : 11721099264 (11178.11 GiB 12002.41 GB)
   Raid Devices : 9
  Total Devices : 9
Preferred Minor : 0

    Update Time : Sat May 28 00:02:49 2011
          State : clean
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 3306f2fe - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8        0        3      active sync   /dev/sda
   4     4       8       48        4      active sync   /dev/sdd
   5     5       8      144        5      active sync   /dev/sdj
   6     6       8      128        6      active sync   /dev/sdi
   7     7       8      112        7      active sync   /dev/sdh
   8     8       8       96        8      active sync   /dev/sdg

Notice the size difference? I have the drives in the correct order after the rebuild but it's saying the size discrepancy is blocking me from fsck'ing the file system.

My question is, is my data screwed because I recreated with the 1.2 meta data when it was a 0.90 array initially? If not is there some explanation to the size discrepency that I can correct?

Any help to get this recovered would be greatly appreciate :(

fsck'ing results in: 


fsck.ext4: Group descriptors look bad... trying backup blocks...
The filesystem size (according to the superblock) is 2930276864 blocks
The physical size of the device is 2930274816 blocks
Either the superblock or the partition table is likely to be corrupt!

---


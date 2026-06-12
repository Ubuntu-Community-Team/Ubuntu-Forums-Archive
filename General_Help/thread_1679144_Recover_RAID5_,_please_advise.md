---
title: "Recover RAID5 , please advise"
date: 2011-01-31
forum: General Help
---

### Post by JuntaD on 2011-01-31
Dear Linux community;

Could any RAID gurus kindly  assist me on the following RAID-5 issue?
I have an mdadm-created RAID5 array consisting of 4 discs. One of the discs was dropping out, so I decided to replace it. Somehow, this went terribly wrong and I succeeded in marking two of the drives as faulty, and the re-adding them as spare. 

Now the array is (logically) no longer able to start:

mdadm: Not enough devices to start the array.
Degraded and can't create RAID ,auto stop RAID [md1]

I was able to examine the disks though:

```

root@127.0.0.1:/etc# mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a15dbaf1:0e703d8a:6704b3cf:ca9c3527
  Creation Time : Mon Aug  2 02:48:53 2010
     Raid Level : raid5
  Used Dev Size : 1951552000 (1861.15 GiB 1998.39 GB)
     Array Size : 5854656000 (5583.44 GiB 5995.17 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Jan 29 11:25:36 2011
          State : clean
 Active Devices : 2
Working Devices : 4
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 9979745e - correct
         Events : 0.7829440

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       0        0        1      faulty removed
   2     2       8       50        2      active sync   /dev/sdd2
   3     3       0        0        3      faulty removed
   4     4       8        2        4      spare   /dev/sda2
   5     5       8       34        5      spare   /dev/sdc2


```I think the array can still be saved, as no disc actually died on me. I was reading the Linux Raid Recovery Wiki; and thought that the solution could be this:

```

mdadm --create --assume-clean --level=5 --**raid**-devices=4 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2

```As I don't want to ruin the maybe small chance I have left to rescue my data, I would like to hear the input of this wise community :)

Many thanks in advance for helping a desperate fool!

Kind regards,

Junta D.

---


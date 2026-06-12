---
title: "re-build mdadm RAID"
date: 2010-10-11
forum: General Help
---

### Post by pantmerchant on 2010-10-11
Hi, i'm a bit of a mdadm noob and am hung up on re-building a RAID (6 drives, 5 +1 spare). I have one drive failed. I deleted the mdadm.conf file to try and re-build it, but now after running sudo mdadm --assemble --scan it returns

mdadm: No arrays found in config file

So i'm foggy on how to re-assemble the raid, below is the output of sudo mdadm --examine

sudo mdadm --examine /dev/sda/:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d3fa4613:7d107bf3:23869138:3588d00b
  Creation Time : Sun Dec  6 17:10:23 2009
     Raid Level : raid5
  Used Dev Size : 244198464 (232.89 GiB 250.06 GB)
     Array Size : 1220992320 (1164.43 GiB 1250.30 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Wed Oct  6 16:33:19 2010
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 1
       Checksum : f99d35c5 - correct
         Events : 1392

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       16        6      spare   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       80        5      active sync   /dev/sdf
   6     6       8       16        6      spare   /dev/sdb

Thanks in advance!

---


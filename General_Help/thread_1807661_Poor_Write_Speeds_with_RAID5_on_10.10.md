---
title: "Poor Write Speeds with RAID5 on 10.10"
date: 2011-07-19
forum: General Help
---

### Post by not_the_messiah on 2011-07-19
Hi,

I am getting extremely poor write speeds with my RAID. My setup is as follows:
> HP Proliant Microserver
> 4 2TB Samsung F4 drives
> 60GB root drive
> Ubuntu 10.10 64bit
> mdadm 3.2.2

I have two of the above servers, connected via gigabit LAN. The read speeds I am happy with, but write speeds are running at about 20Mb/s at the very best, which I don't think is that great. Especially when people with a similar setup on a machine like this are running at about 90MB/s write speeds...

My array is as follows (mdadm --detail -D /dev/md0):
> /dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 18 22:36:01 2011
     Raid Level : raid5
     Array Size : 5860531200 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Tue Jul 19 15:30:29 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : tim-ProLiant-MicroServer:0  (local to host tim-ProLiant-MicroServer)
           UUID : 95e90209:102debea:33a66f2c:b903e0af
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1


I have also started the partitions at 64 instead of 63 in a bid to correctly align the partitions, although this doesn't seem to have made any difference.

Can anyone offer any advice as I have been at this for days now, tearing down, rebuild etc, to no avail :(

Thanks in advance.

Tim

---

### Post by not_the_messiah on 2011-07-20
*Bump*

---

### Post by nipennem on 2011-07-31
Did you only test the performance over the network? Try eliminating the network and benchmark the filesystem or the RAID block device on the server.

---

### Post by zitch on 2011-07-31
Due to the nature of how RAID 5 works (because of the parity bit calculations required, every write will need at least a read from two drives to calculate the new parity bit before the write), my own inferences and experience is that RAID 5 will simply be much slower on writes. Basically, the way I see it, only use RAID 5 if you don't care about write performance at all, otherwise, go RAID 1+0.

Basically, what are your read speeds at compared to your writes with the RAID 5 setup?  Then reconfigure the server in a RAID 1+0 setup and compare your read speeds with the write speeds then.  I'd suspect the write vs. read numbers will be much closer on the RAID 1+0 than on the RAID 5.

---

### Post by nipennem on 2011-07-31
> **zitch said:**
> Due to the nature of how RAID 5 works (because of the parity bit calculations required, every write will need at least a read from two drives to calculate the new parity bit before the write), my own inferences and experience is that RAID 5 will simply be much slower on writes. Basically, the way I see it, only use RAID 5 if you don't care about write performance at all, otherwise, go RAID 1+0.

Basically, what are your read speeds at compared to your writes with the RAID 5 setup?  Then reconfigure the server in a RAID 1+0 setup and compare your read speeds with the write speeds then.  I'd suspect the write vs. read numbers will be much closer on the RAID 1+0 than on the RAID 5.

Even the read speeds are too slow to be normal for md raid5. Once again, benchmark without the network, and check the CPU usage during writes.

---


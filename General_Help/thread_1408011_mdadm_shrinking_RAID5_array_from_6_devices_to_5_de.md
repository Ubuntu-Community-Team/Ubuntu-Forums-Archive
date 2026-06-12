---
title: "mdadm shrinking RAID5 array from 6 devices to 5 devices"
date: 2010-02-15
forum: General Help
---

### Post by Qwerty9119 on 2010-02-15
Hello All,

I have a problem with my mdadm RAID. I wanted to know if anyone had any experience with shrinking RAID5 arrays. I was growing the array from 5 to 6 devices however the grow got interrupted and it has recovered to 5 drives. The 6th drive is toast and I am unable to re add it to the system.

I would like to drive the device listed as "removed". I have tried mdadm /dev/md0 --remove detached and failed with no success.

I am running Ubuntu kernel 2.6.28-11 and mdadm is v3.1.1.

Any suggestions would be much appreciated.

Here is output of a "mdadm -D dev/md0"

/dev/md0:
Version : 0.90
Creation Time : Wed Jan 12 00:46:41 2009
Raid Level : raid5
Array Size : 4883812480 (4657.57 GiB 5001.02 GB)
Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
Raid Devices : 6
Total Devices : 5
Preferred Minor : 0
Persistence : Superblock is persistent

Update Time : Mon Feb 15 20:25:07 2010
State : active, degraded
Active Devices : 5
Working Devices : 5
Failed Devices : 0
Spare Devices : 0

Layout : left-symmetric
Chunk Size : 64K

UUID : 74fa5199:84b88e81:4ae0fbae:92643084
Events : 0.1331010

Number Major Minor RaidDevice State
0 8 16 0 active sync /dev/sdb
1 8 32 1 active sync /dev/sdc
2 8 48 2 active sync /dev/sdd
3 8 0 3 active sync /dev/sda
4 8 64 4 active sync /dev/sde
5 0 0 5 removed


cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdb[0] sde[4] sda[3] sdd[2] sdc[1]
4883812480 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUUUU_]

unused devices: <none>

---


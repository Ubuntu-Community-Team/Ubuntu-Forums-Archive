---
title: "disk utility, raid 5 and used dev size"
date: 2011-02-11
forum: General Help
---

### Post by samcoinc on 2011-02-11
Hello.  I am runnig ubuntu 10.04 lts

I created a raid 5 using the disk utillity on a 8 drive esata box.  The issue I have is that for some reason - the used dev size is twice what it should be.  What am I doing wrong.  I created something similar on another box using command line and its used dev size is 1 drive.

I have created 2 different arrrays using the gui and both seem to have the used dev size as twice what it should be.  Am I missing something?

```
1./dev/md1:
2.        Version : 01.02
3.  Creation Time : Thu Feb 10 16:50:37 2011
4.     Raid Level : raid5
5.     Array Size : 6837318656 (6520.58 GiB 7001.41 GB)
6.  Used Dev Size : 1953519616 (1863.02 GiB 2000.40 GB)
7.   Raid Devices : 8
8.  Total Devices : 8
9.Preferred Minor : 1
10.    Persistence : Superblock is persistent
11. 
12.  Intent Bitmap : Internal
13. 
14.    Update Time : Fri Feb 11 10:57:27 2011
15.          State : active
16. Active Devices : 8
17.Working Devices : 8
18. Failed Devices : 0
19.  Spare Devices : 0
20. 
21.         Layout : left-symmetric
22.     Chunk Size : 64K
23. 
24.           Name : :Array8
25.           UUID : c7d5869a:775e0cec:4f595f82:22f22e3e
26.         Events : 24214
27. 
28.    Number   Major   Minor   RaidDevice State
29.       0      65        1        0      active sync   /dev/sdq1
30.       1       8      241        1      active sync   /dev/sdp1
31.       2       8      225        2      active sync   /dev/sdo1
32.       3       8      209        3      active sync   /dev/sdn1
33.       4       8      193        4      active sync   /dev/sdm1
34.       5       8      177        5      active sync   /dev/sdl1
35.       6       8      161        6      active sync   /dev/sdk1
36.       8       8      145        7      active sync   /dev/sdj1
```

---


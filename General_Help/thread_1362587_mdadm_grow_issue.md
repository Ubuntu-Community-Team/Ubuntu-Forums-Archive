---
title: "mdadm grow issue"
date: 2009-12-23
forum: General Help
---

### Post by nairb11 on 2009-12-23
I know this is an mdadm help issue, not ubuntu, I hope its ok to post it here.

I'm using Intrepid and mdadm 2.6.7.

I had a clean stable raid5 array, 5x1tb, before I started.  I decided to add another 1tb drive to the array because space was getting low.

I connected the new drive and issued the following commands:

```
sudo mdadm --add /dev/md0 /dev/sdg
sudo mdadm --grow /dev/md0 --raid-devices=6
```

cat /proc/mdstat showed it was going to take ~1600 minutes so I went to bed.  When I woke up I had mail with the following:

```
A Fail event had been detected on md device /dev/md0.
It could be related to component device /dev/sdf
```

The array was now reshaping and listed /dev/sdf as a faulty spare.  I let it finish the reshape which ended with a faulty spare, failed device.  

Next,

```
sudo mdadm --manage /dev/md0 --remove /dev/sdf
```

Now I my status shows the following:

cat /proc/mdstat:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[0] sdg[5] sdb1[3] sdd1[2] sdc1[1]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUUU_U]
```

sudo mdadm --detail /dev/md0:
```
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  9 00:03:20 2009
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Dec 23 08:41:34 2009
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 48c840d0:ef028c1b:500c5acc:68ce6167 (local to host eleven)
         Events : 0.1299120

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       17        3      active sync   /dev/sdb1
       4       0        0        4      removed
       5       8       96        5      active sync   /dev/sdg

```

So my question is, did the grow operation finish, and I just need to add a new drive and let it reshape, then extend my filesystem?

Could I grow (shrink) to one less drive and be back to where I started?

---

### Post by Fcon_Vpro on 2009-12-28
From what I can see, the array is showing as 5TB so it looks like the grow finished and you just need to add another drive and let it reshape and everything should be ok. 
Did you unmount the array before you did the grow?

---

### Post by nairb11 on 2009-12-28
Yea, I went ahead and put a new drive in and added it to the arry, it rebuilt in about 2 hours, after I resized the fs everything was the way it should be.  I guess it was just bad timing for a drive to die, but mdadm handled it perfectly and nothing was lost.

---


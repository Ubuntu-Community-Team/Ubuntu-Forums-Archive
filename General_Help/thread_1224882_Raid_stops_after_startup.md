---
title: "Raid stops after startup"
date: 2009-07-27
forum: General Help
---

### Post by ViPeRaY on 2009-07-27
Hey folks,
 
I am testing Ubuntu Server with raid to understand how exactly raid works on ubuntu. So far it has been good. I understood the applications (fdisk, mdadm etc.) I not new to Ubuntu but i am not a pro neither.
 
I set up a raid1 wit two HD. So far everything works fine, no errors. However after every restart, the array stops working. Please see /proc/mdstat output before and after the restart below.
```

MDSTAT BEFORE RESTART
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md1 : active raid1 sdb1[0] sdc1[1]
      16771712 blocks [2/2] [UU]
 
unused devices: <none>

```
 
```

MDSTAT AFTER RESTART
 
 Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md_d1 : inactive sdc1[1](S)
      16771712 blocks
 
unused devices: <none>

```
 
To make raid usable after restart, i try assemble them with the command below.
 
mdadm --assemble --scan --uuid=3b1a2915:d91c9a66:a31daec1:a2180fa4
 
But some reason, raid only picks up one hard drive. The second hard drive does not seem UP, please see below.
 
```

MDSTAT AFTER THE ASSEMBLE COMMAND
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md1 : active raid1 sdb1[0]
      16771712 blocks [2/1] [U_]
 
md_d1 : inactive sdc1[1](S)
      16771712 blocks
 
unused devices: <none>

```
 
```

THIS IS THE OUTPUT OF COMMAND BELOW AFTER I ASSEMBLE THE RAID.
 
viper@UServerTST:/mnt/md1$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Mon Jul 27 20:46:40 2009
     Raid Level : raid1
     Array Size : 16771712 (15.99 GiB 17.17 GB)
  Used Dev Size : 16771712 (15.99 GiB 17.17 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent
    Update Time : Mon Jul 27 21:30:21 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
           UUID : 3b1a2915:d91c9a66:a31daec1:a2180fa4 (local to host UServerTST)
         Events : 0.8
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed

```
 
As you see after restart raid does not come online. If i try to assemble them manually, the second HD shows as removed. Do you have any idea what is wrong?
 
Also if i try below to add the HD to the array manually:
```

viper@UServerTST:/mnt/md1$ sudo mdadm /dev/md1 -a /dev/sdc1 
mdadm: Cannot open /dev/sdc1: Device or resource busy

```
I get the busy error as you see. Well I will be building a file server this week and I need to figure out what is going on. Also this is a test environment. Everything is on vmware. Do you think raid is failing because it is not running on real hardware?
 
I appriciate your help. Thanks,

---

### Post by ViPeRaY on 2009-07-28
I am sorry i was supposed to post this under Server Platforms forum. Can somebody move this thread please?
 
Thanks a lot.

---


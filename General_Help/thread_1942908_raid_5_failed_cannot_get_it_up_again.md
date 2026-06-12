---
title: "raid 5 failed cannot get it up again"
date: 2012-03-18
forum: General Help
---

### Post by syn4pse on 2012-03-18
Hello,
I was on holidays and could not login from there, when i came home I realised something was wrong with my pc, I quickly found out the raid could not start up. its a raid 5 consisting of 5 disks each 2TB. So heres my output maybe you guys know what to do

checking status ( seeing all 5 disks )
```
loeken-pc ~ # cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1](S) sdf1[5](S) sde1[3](S) sdd1[2](S) sdc1[0](S)
      9767562680 blocks super 1.2
       
unused devices: <none>
```so i decided to start it:
```
loeken-pc ~ # mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error

```after that error came up i looked again at the status and now sdc1 is gone
```
l
loeken-pc ~ # cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1] sdf1[5] sde1[3] sdd1[2]
      7814050144 blocks super 1.2
       
unused devices: <none>
```I also found erros showing up in dmesg:
```
loeken-pc ~ # dmesg |grep sdc
[    1.805445] sd 1:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.805447] sd 1:0:0:0: [sdc] 4096-byte physical blocks
[    1.805492] sd 1:0:0:0: [sdc] Write Protect is off
[    1.805493] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.805504] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.821310]  sdc: sdc1
[    1.821734] sd 1:0:0:0: [sdc] Attached SCSI disk
[    1.983387] md: bind<sdc1>
[   96.473877] md: kicking non-fresh sdc1 from array!
[   96.473888] md: unbind<sdc1>
[   96.519892] md: export_rdev(sdc1)
```this to ensure its really set as failed
```
loeken-pc ~ # mdadm /dev/md0 --fail /dev/sdc1
mdadm: set device faulty failed for /dev/sdc1:  No such device
```trying to remove it from the raid
```
loeken-pc ~ # mdadm /dev/md0 --remove /dev/sdc1
mdadm: hot remove failed for /dev/sdc1: No such device or address
```tryin to readd it to raid:
```
loeken-pc ~ # mdadm /dev/md0 --add /dev/sdc1
mdadm: add new device failed for /dev/sdc1 as 6: Invalid argument
```another detailed view:
```

loeken-pc ~ # mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Aug 19 23:32:18 2011
     Raid Level : raid5
  Used Dev Size : 1953509376 (1863.01 GiB 2000.39 GB)
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Mar 11 03:56:35 2012
          State : active, degraded, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4096K

           Name : loeken-pc:0  (local to host loeken-pc)
           UUID : 674a53cf:472a4b47:fece48bc:b091fda9
         Events : 261

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       5       8       81        4      active sync   /dev/sdf1

```
any kind of help is appreciated a lot.

---

### Post by syn4pse on 2012-03-18
i think i got it working its reconstructing

```

loeken-pc ~ # mdadm --stop  /dev/md0
mdadm: stopped /dev/md0
loeken-pc ~ # mdadm --assemble --force  /dev/md0
mdadm: /dev/md0 has been started with 4 drives (out of 5) and 1 spare.
loeken-pc ~ # cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sdc1[6] sdf1[5] sde1[3] sdd1[2]
      7814037504 blocks super 1.2 level 5, 4096k chunk, algorithm 2 [5/4] [_UUUU]
      [>....................]  recovery =  0.0% (474412/1953509376) finish=1921.1min speed=16943K/sec
      
unused devices: <none>

```

---


---
title: "mdam - broken raid 10"
date: 2011-08-01
forum: General Help
---

### Post by nicocampo on 2011-08-01
Hello,

Today I have a problem with mdadm, my raid doesn't work anymore. This is a RAID 10 made of 4 partitions.

When I try to manually assemble devices using the following command :

```

mdadm -A /dev/md0 /dev/sda3 /dev/sdb6 /dev/sdc6 /dev/sdd6

```it says

```

mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```Then, mdstat says :

```

root@fractal:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc6[2](S) sdd6[3](S) sdb6[1](S) sda3[0](S)
      606196224 blocks

unused devices: <none>


```When I print details about each partitions, the first 2 (sda3 and sdb6) seem ok, and we can see in the summary at the end that they "see" other devices, sdc6 and sdd6 as "active".

```

root@fractal:~# mdadm -E /dev/sda3
/dev/sda3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7a2ec89:28b8552c:ec193043:a0358490 (local to host fractal)
  Creation Time : Sun Oct  3 12:53:20 2010
     Raid Level : raid10
  Used Dev Size : 151548928 (144.53 GiB 155.19 GB)
     Array Size : 303097856 (289.06 GiB 310.37 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Aug  1 10:03:55 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f9c7841a - correct
         Events : 230500

         Layout : near=1, far=2
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8        3        0      active sync   /dev/sda3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       22        1      active sync   /dev/sdb6
   2     2       8       38        2      active sync   /dev/sdc6
   3     3       8       54        3      active sync   /dev/sdd6

``````

root@fractal:~# mdadm -E /dev/sdb6
/dev/sdb6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7a2ec89:28b8552c:ec193043:a0358490 (local to host fractal)
  Creation Time : Sun Oct  3 12:53:20 2010
     Raid Level : raid10
  Used Dev Size : 151548928 (144.53 GiB 155.19 GB)
     Array Size : 303097856 (289.06 GiB 310.37 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Aug  1 10:03:55 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f9c7842f - correct
         Events : 230500

         Layout : near=1, far=2
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     1       8       22        1      active sync   /dev/sdb6

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       22        1      active sync   /dev/sdb6
   2     2       8       38        2      active sync   /dev/sdc6
   3     3       8       54        3      active sync   /dev/sdd6

```But when we ask details for the 2 other devices, we see errors

```

root@fractal:~# mdadm -E /dev/sdc6
/dev/sdc6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7a2ec89:28b8552c:ec193043:a0358490 (local to host fractal)
  Creation Time : Sun Oct  3 12:53:20 2010
     Raid Level : raid10
  Used Dev Size : 151548928 (144.53 GiB 155.19 GB)
     Array Size : 303097856 (289.06 GiB 310.37 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Aug  1 10:08:16 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f9c78564 - correct
         Events : 230504

         Layout : near=1, far=2
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     2       8       38        2      active sync   /dev/sdc6

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       38        2      active sync   /dev/sdc6
   3     3       8       54        3      active sync   /dev/sdd6

``````
root@fractal:~# mdadm -E /dev/sdd6
/dev/sdd6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7a2ec89:28b8552c:ec193043:a0358490 (local to host fractal)
  Creation Time : Sun Oct  3 12:53:20 2010
     Raid Level : raid10
  Used Dev Size : 151548928 (144.53 GiB 155.19 GB)
     Array Size : 303097856 (289.06 GiB 310.37 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Aug  1 10:08:16 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f9c78576 - correct
         Events : 230504

         Layout : near=1, far=2
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     3       8       54        3      active sync   /dev/sdd6

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       38        2      active sync   /dev/sdc6
   3     3       8       54        3      active sync   /dev/sdd6

```How can I get this raid working back again ? I hope I will, so many important work in there :(

Thank you

---

### Post by nicocampo on 2011-08-01
Ok, raid is back.

Following this (french) documentation : [http://hoper.dnsalias.net/tdc/index.php?post/2010/06/18/Quand-il-n-y-a-plus-aucun-espoir](http://hoper.dnsalias.net/tdc/index.php?post/2010/06/18/Quand-il-n-y-a-plus-aucun-espoir)

I first **forced **assembly of the 3 first members :

```

root@fractal:~# mdadm --assemble --force /dev/md0 /dev/sda3 /dev/sdb6 /dev/sdc6
mdadm: forcing event count in /dev/sda3(0) from 230500 upto 230504
mdadm: forcing event count in /dev/sdb6(1) from 230500 upto 230504
mdadm: /dev/md0 has been started with 3 drives (out of 4).

```Check everything is ok

```

root@fractal:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid10 sda3[0] sdc6[2] sdb6[1]
      303097856 blocks 256K chunks 2 far-copies [4/3] [UUU_]

```Then add the fouth member

```

mdadm --add /dev/md0 /dev/sdd

```And just watch the job completing

```

root@fractal:~# watch cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid10 sdd6[4] sda3[0] sdc6[2] sdb6[1]
      303097856 blocks 256K chunks 2 far-copies [4/3] [UUU_]
      [>....................]  recovery =  0.1% (225920/151548928) finish=33.4min speed=75306K/sec

```

---


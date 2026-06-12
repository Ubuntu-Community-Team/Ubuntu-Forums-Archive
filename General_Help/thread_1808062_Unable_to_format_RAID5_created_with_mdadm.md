---
title: "Unable to format RAID5 created with mdadm"
date: 2011-07-19
forum: General Help
---

### Post by AllGamer on 2011-07-19
This is the error message I'm getting when trying to Format the **mdadm** **RAID5** created with 4 drives 
```

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/md1, start=0, size=6001196531712, type=
Entering MS-DOS parser (offset=0, size=6001196531712)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
GPT magic found
partition_entry_lba=2
num_entries=128
size_of_entry=128
Leaving EFI GPT parser
EFI GPT partition table detected
containing partition table scheme = 3
got it
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Warning: Not all of the space available to /dev/md1 appears to be used, you can fix the GPT to use all of the space (an extra 7814057808 blocks) or continue with the current setting? 
got disk
new partition
guid '' is not valid
type '' for GPT appear to be malformed

```


this is the command used; which worked on another machine witht he exact same configuration

```

sudo mdadm --create /dev/md1 --level=5 --raid-devices=4 /dev/sde /dev/sdf /dev/sdg /dev/sdh

```
and it returned
```

mdadm: array /dev/md1 started.

```

if i do a status check i get this
```

sudo mdadm -Q -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Tue Jul 19 20:59:03 2011
     Raid Level : raid5
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Jul 19 20:59:05 2011
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 24f2813f:9bd647f7:4b5ead09:bbb9f317  
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       8       80        1      active sync   /dev/sdf
       2       8       96        2      active sync   /dev/sdg
       4       8      112        3      spare rebuilding   /dev/sdh

```

Do i have to wait for it to finish rebuilding before i can Format the RAID with ext4 ?:confused:

---

### Post by AllGamer on 2011-07-19
here's an exact same one that i created on another machine using the same drives and same commands

```

sudo mdadm -Q -D /dev/md0

/dev/md0:
        Version : 00.90
  Creation Time : Mon May  9 17:07:54 2011
     Raid Level : raid5
     Array Size : 5860540224 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jul 19 21:15:09 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1509f2f1:33aa139d:a8940a20:3aca4cc2 
         Events : 0.81

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

on that instance i was able to format the raid to ext4 right away

---

### Post by coffee412 on 2011-07-19
Wait until its done rebuilding. Then you can go ahead and format it.

---

### Post by AllGamer on 2011-07-21
seems like my brain conveniently dismissed the boring memories of waiting forever for the RAID to finish syncing/rebuilding before being able to format the drive

LOL :D

---


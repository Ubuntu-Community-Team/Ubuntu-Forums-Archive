---
title: "Help Restoring Raid With mdadm"
date: 2011-10-19
forum: General Help
---

### Post by dudemanbubba on 2011-10-19
I upgraded my 8.04 server to 10.04 with a fresh install.  I had a raid 1 using mdadm on the previous server.  The fresh install put dmraid on there which I didn't like.  I removed the dmraid and removed the metadata.  I installed mdadm and assembled the raid.  It is running but the second drive does not appear to be active.  The following is the output from mdadm --detail:

```
administrator@dcls1:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Feb 24 16:00:30 2010
     Raid Level : raid1
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct 19 09:31:46 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 8a35b533:3867ee91:8d6f267d:6778b5a1 (local to host dcls1)
         Events : 0.774

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed

```fdisk -l looks like:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       37437   300706816   83  Linux
/dev/sda2           37437       38914    11862017    5  Extended
/dev/sda5           37437       38914    11862016   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74245bc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdbb35644

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 4016 MB, 4016045568 bytes
124 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a90a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1020     3920849    c  W95 FAT32 (LBA)

Disk /dev/md_d0: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md_d0 doesn't contain a valid partition table

Disk /dev/md0: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```I have tried removing and adding the drive again.  When I try to add the drive it tells me "Cannot open /dev/sdc1:  Device or resource busy".  Not sure where to go to get this resolved.

Any help would be appreciated.

Thanks.

---


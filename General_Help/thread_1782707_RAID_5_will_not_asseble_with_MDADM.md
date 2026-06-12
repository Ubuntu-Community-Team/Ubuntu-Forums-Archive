---
title: "RAID 5 will not asseble with MDADM"
date: 2011-06-14
forum: General Help
---

### Post by zac_haryy on 2011-06-14
I cant seem to get my RAID 5 (consisting of 8 1tb hard drives) assembled for some reason and I have no idea why and cant find any solutions online. Ill go ahead and show what my problem is:

here is all my hard drives:
```
server:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f041

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1186     9526513+  83  Linux
/dev/sda2            1187        1245      473917+   5  Extended
/dev/sda5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b38a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4927a974

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2edd36e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f28f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c4be00f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00069a45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4927a977

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

```

If I try assemble the array I get this:
```
server:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.

```

So then I examine each drive and get this: (in groups of two)
```
server:~$ sudo mdadm -E /dev/sdb1 /dev/sdc1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:11:38 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 4
  Spare Devices : 0
       Checksum : dfea8ae7 - correct
         Events : 0.1451200

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8       17        7      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:11:38 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 4
  Spare Devices : 0
       Checksum : dfea8af5 - correct
         Events : 0.1451200

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       33        6      active sync   /dev/sdc1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1

```

```
server:~$ sudo mdadm -E /dev/sdd1 /dev/sde1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:11:38 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 4
  Spare Devices : 0
       Checksum : dfea8af9 - correct
         Events : 0.1451200

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:11:38 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 4
  Spare Devices : 0
       Checksum : dfea8b13 - correct
         Events : 0.1451200

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       65        5      active sync   /dev/sde1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1

```

```
server:~$ sudo mdadm -E /dev/sdf1 /dev/sdg1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:06:28 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dfea8985 - correct
         Events : 0.1451195

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       81        2      active sync   /dev/sdf1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8      129        4      active sync   /dev/sdi1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:06:28 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dfea8993 - correct
         Events : 0.1451195

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       97        1      active sync   /dev/sdg1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8      129        4      active sync   /dev/sdi1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1

```

```
server:~$ sudo mdadm -E /dev/sdh1 /dev/sdi1
/dev/sdh1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:06:28 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dfea89a7 - correct
         Events : 0.1451195

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      113        3      active sync   /dev/sdh1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8      129        4      active sync   /dev/sdi1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1
/dev/sdi1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Jun  9 20:06:28 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : dfea89b9 - correct
         Events : 0.1451195

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8      129        4      active sync   /dev/sdi1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8      113        3      active sync   /dev/sdh1
   4     4       8      129        4      active sync   /dev/sdi1
   5     5       8       65        5      active sync   /dev/sde1
   6     6       8       33        6      active sync   /dev/sdc1
   7     7       8       17        7      active sync   /dev/sdb1

```

So as you can see the array for those last four look fine however for the first four it marks the last four drives as faulty for some reason. I am kind of clueless to do from this point on honestly, I have data on this array that I'd really like to save. Please help me out, thank you!

-haryy

---

### Post by tgalati4 on 2011-06-15
Are these "Green" drives?

---

### Post by zac_haryy on 2011-06-15
> **tgalati4 said:**
> Are these "Green" drives?

Lol yes they are WD "green" drives.

---

### Post by zac_haryy on 2011-06-15
For the record I had somebody over on another forum suggest this:

> Try the following:

sudo mdadm --assemble --scan /dev/md0 .... so on

if that does not work then try it with -f (force) switch:

sudo mdadm --assemble --scan -f /dev/md0 .... so on

I hope you have the backup of the data in case you are not able to get the RAID backup correctly.

Yes this worked like a charm. I've tried assembling this with the force command but listing the individual drives instead of using scan.

Here is the the output from the commands:
```
@server:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
@server:~$ sudo mdadm --assemble --scan /dev/md0
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
@server:~$ sudo mdadm --assemble --scan -f /dev/md0
mdadm: forcing event count in /dev/sdg1(1) from 1451195 upto 1451200
mdadm: forcing event count in /dev/sdf1(2) from 1451195 upto 1451200
mdadm: forcing event count in /dev/sdh1(3) from 1451195 upto 1451200
mdadm: forcing event count in /dev/sdi1(4) from 1451195 upto 1451200
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdg1
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sdf1
mdadm: clearing FAULTY flag for device 1 in /dev/md0 for /dev/sdh1
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdi1
mdadm: /dev/md0 has been started with 8 drives.

```

---

### Post by tgalati4 on 2011-06-16
My understanding is that "green" drives can be problematic with RAID because they shut down (to save power) and RAID expects them to be operating 24/7.  You can probably use them in JBOD (just a bunch of disks) configuration with a script to perform periodic mirroring or backup or rsync.

Please update this thread when you get ready to throw them out the window.

---


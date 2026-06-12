---
title: "Mounting mdadm arrays from live CD?"
date: 2011-03-10
forum: General Help
---

### Post by Fraoch on 2011-03-10
I'm trying to mount existing mdadm arrays off a 10.10 install from the live CD.  I copied my existing mdadm.conf since it was on an mdadm-administered partition to a normal partition so it could be read while in the live CD environment.

While in the live CD environment, I installed mdadm, then tried:

```
sudo mdadm --assemble --scan
```

(found this command by searching)

However I get:

```
mdadm: no devices found for /dev/md1
mdadm: no devices found for /dev/md0
```

This command uses mdadm.conf which specifies devices by UUID.  The partially-recognized RAID components do not have UUIDs, so I tried manually by specifying:

```
sudo mdadm --assemble /dev/md1 /dev/sda3 /dev/sdb2
```

following careful examination of what partitions are included in each RAID device.  But I get:

```
mdadm: cannot open device /dev/sda3: No such file or directory
mdadm: /dev/sda3 has no superblock - assembly aborted
```

It's true that there is no /dev/sda3, but then why does fdisk -l give me this?

```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e5dcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4441        4500      481950   83  Linux
/dev/sda2            4319        4440      979965   82  Linux swap / Solaris
/dev/sda3            2131        4318    17575110   fd  Linux raid autodetect
/dev/sda4               1        2130    17109193+  fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf904f904

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4380        4500      971932+  82  Linux swap / Solaris
/dev/sdb2            2192        4379    17575110   fd  Linux raid autodetect
/dev/sdb3              64        2191    17093160   fd  Linux raid autodetect
```

There are RAID components in /dev/dm-0, /dev/dm-2, /dev/dm-3 and /dev/dm-4, recognised by the kernel I believe, but when I try:

```
sudo mdadm --assemble /dev/md1 /dev/dm-3 /dev/dm-4
```

I get:

```
mdadm: no recogniseable superblock on /dev/dm-3
mdadm: /dev/dm-3 has no superblock - assembly aborted
```

But this RAID 0 array is running perfectly on the installed system, it sure should have superblocks.

:confused:

Thanks for any advice.

---

### Post by rubylaser on 2011-03-10
Why don't you verify that there are superblocks with the mdadm -E command?
```
mdadm -E /dev/sda3
```
And do that for all your partitions that show up in fdisk -l as linux raid autodetect.  Please paste the results.

It will show you something like this if a superblock exists...
```
root@nas:~# mdadm -E /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 659d1429:3055e9ed:806f9f3f:b5caed45
  Creation Time : Sun Sep  5 20:08:17 2010
     Raid Level : raid6
  Used Dev Size : 488382912 (465.76 GiB 500.10 GB)
     Array Size : 1953531648 (1863.03 GiB 2000.42 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Thu Mar 10 09:56:23 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2c76d929 - correct
         Events : 123334

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1

```

---

### Post by Fraoch on 2011-03-10
> **rubylaser said:**
> ```
root@nas:~# mdadm -E /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 659d1429:3055e9ed:806f9f3f:b5caed45
  Creation Time : Sun Sep  5 20:08:17 2010
     Raid Level : raid6
  Used Dev Size : 488382912 (465.76 GiB 500.10 GB)
     Array Size : 1953531648 (1863.03 GiB 2000.42 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Thu Mar 10 09:56:23 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2c76d929 - correct
         Events : 123334

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1

```

It gives me output like that from the running install, say for my /dev/sda3, but from the live CD, it indicates no such file in /dev.  Note the drives are rearranged a bit, sda = sdb and sdb = sdc in the live CD, but I've verified several times that they are the arrays in question:

```
ubuntu@ubuntu:~$ mdadm -E /dev/sdb3
mdadm: cannot open /dev/sdb3: No such file or directory
ubuntu@ubuntu:~$ mdadm -E /dev/sdb4
mdadm: cannot open /dev/sdb4: No such file or directory
ubuntu@ubuntu:~$ mdadm -E /dev/sdc2
mdadm: cannot open /dev/sdc2: No such file or directory
ubuntu@ubuntu:~$ mdadm -E /dev/sdc3
mdadm: cannot open /dev/sdc3: No such file or directory
```

I also have /dev/dm-X drives in /dev, I think these are detected by the kernel RAID driver, but these have no superblocks:

```
ubuntu@ubuntu:~$ sudo mdadm -E /dev/dm-0
mdadm: No md superblock detected on /dev/dm-0.
ubuntu@ubuntu:~$ sudo mdadm -E /dev/dm-2
mdadm: No md superblock detected on /dev/dm-2.
ubuntu@ubuntu:~$ sudo mdadm -E /dev/dm-3
mdadm: No md superblock detected on /dev/dm-3.
ubuntu@ubuntu:~$ sudo mdadm -E /dev/dm-4
mdadm: No md superblock detected on /dev/dm-4.
```

I'm getting a sneaking suspicion I should mount the drives (sdb and sdc) somehow, but I'm not sure at all how to do that with partial RAID arrays.

I noticed there are partitions within dm-0, as listed in fdisk:

```
Disk /dev/dm-0: 74.0 GB, 74038640640 bytes
255 heads, 63 sectors/track, 9001 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Disk identifier: 0xf904f904

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1            4380        4500      971932+  82  Linux swap / Solaris
Partition 1 does not start on physical sector boundary.
/dev/dm-0p2            2192        4379    17575110   fd  Linux raid autodetect
Partition 2 does not start on physical sector boundary.
/dev/dm-0p3              64        2191    17093160   fd  Linux raid autodetect
Partition 3 does not start on physical sector boundary.

Partition table entries are not in disk order
```

which is odd as the arrays are actually in dm-3 and dm-4.  Based on the start/end numbers, I remember this - dm-0p2 consists of half of array 1 and dm-0p3, half of array 2.  I don't see the other halves of array 1 and array 2 as dm-2, dm-3 and dm-4 do not contain "valid partition tables":

```
Disk /dev/dm-2: 995 MB, 995258880 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Alignment offset: 2560 bytes
Disk identifier: 0xd3e2a660

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 18.0 GB, 17996912640 bytes
255 heads, 63 sectors/track, 2188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Alignment offset: 8704 bytes
Disk identifier: 0xc6eae174

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 17.5 GB, 17503395840 bytes
255 heads, 63 sectors/track, 2128 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Alignment offset: 512 bytes
Disk identifier: 0x9f1da0f7

Disk /dev/dm-4 doesn't contain a valid partition table
```

/dev/dm-0p2 and p3 do not exist in /dev.  /dev/dm-0 does.

```
ubuntu@ubuntu:/dev$ sudo mdadm -E /dev/dm-0p2
mdadm: cannot open /dev/dm-0p2: No such file or directory
ubuntu@ubuntu:/dev$ sudo mdadm -E /dev/dm-0p3
mdadm: cannot open /dev/dm-0p3: No such file or directory
```

Again, I'm thinking I have to mount the drives with the partial arrays, but how?  When I try the traditional way through fstab by adding /dev/sdb and /dev/sdc, it indicates they're already mounted:

```
ubuntu@ubuntu:/dev$ sudo mount -a
mount: /dev/sdb already mounted or /testdrive1 busy
mount: /dev/sdc already mounted or /testdrive2 busy
```

---


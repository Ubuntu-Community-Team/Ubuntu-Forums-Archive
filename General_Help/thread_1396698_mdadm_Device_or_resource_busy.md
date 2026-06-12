---
title: "mdadm Device or resource busy"
date: 2010-02-02
forum: General Help
---

### Post by johj on 2010-02-02
Hi,

I have an existing RAID1 consisting of the 2 disks /dev/sdc and /dev/sdd. However after upgrading to Karmic, one of them fails to be added to the array:

```
$ sudo mdadm --assemble /dev/md0 /dev/sdc /dev/sdd
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has no superblock - assembly aborted
```

At boot time, mdadm detects /dev/mapper/sil_aeahaiccbjag1 instead of /dev/sdX, but I get the same error when I try to assemble the devices in /dev/mapper:

```
$ sudo mdadm --assemble /dev/md0 /dev/mapper/sil_aeahaiccbjag /dev/mapper/sil_aeahaiccbjag1 
mdadm: cannot open device /dev/mapper/sil_aeahaiccbjag: Device or resource busy
mdadm: /dev/mapper/sil_aeahaiccbjag has no superblock - assembly aborted

```

I'm not sure about the differences between /dev/sdX and /dev/mapper/sil_* though, but it seems only the devices in /dev/mapper are recognized by mdadm:

```
$ sudo mdadm -v --misc --examine /dev/sdc 
mdadm: No md superblock detected on /dev/sdc.

$ sudo mdadm -v --misc --examine /dev/sdd 
mdadm: No md superblock detected on /dev/sdd.

$ sudo mdadm -v --misc --examine /dev/mapper/sil_aeahaiccbjag
mdadm: No md superblock detected on /dev/mapper/sil_aeahaiccbjag.

$ sudo mdadm -v --misc --examine /dev/mapper/sil_aeahaiccbjag1 
/dev/mapper/sil_aeahaiccbjag1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b661b5fd:92a6a622:db16827a:775591de
  Creation Time : Thu Jul  8 23:17:29 2004
     Raid Level : raid1
  Used Dev Size : 195358336 (186.31 GiB 200.05 GB)
     Array Size : 195358336 (186.31 GiB 200.05 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Tue Feb  2 15:47:35 2010
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : de9fb1fd - correct
         Events : 16940626


      Number   Major   Minor   RaidDevice State
this     1     252        1        1      active sync   /dev/block/252:1

   0     0       0        0        0      removed
   1     1     252        1        1      active sync   /dev/block/252:1
```


The devices are also listed differntly by blkid:

```
/dev/sdc: TYPE="silicon_medley_raid_member" 
/dev/sdd: TYPE="silicon_medley_raid_member" 
/dev/mapper/sil_aeahaiccbjag1: UUID="b661b5fd-92a6-a622-db16-827a775591de" TYPE="linux_raid_member" 
```


Can anyone enlighten me as to why /dev/mapper/sil_aeahaiccbjag1 is recognized as a linux_raid_member while /dev/sdc or /dev/sdd are not?

Furthermore, why is the sdc device busy? It's certainly not mounted already...

Some system info:
Ubuntu Karmic 64-bit
Linux 2.6.31-17-generic


- Johannes

---

### Post by johj on 2010-02-13
I finally found the problem - the dmraid-driver had taken control of the devices:

[http://en.wikipedia.org/wiki/Mdadm#Known_problems](http://en.wikipedia.org/wiki/Mdadm#Known_problems)

I fixed it by removing the dmraid and libdmraid1.0.0.rc15 packages as described on:

[http://superuser.com/questions/102086/how-to-build-initrd-without-dmraid-driver-on-ubuntu-9-10](http://superuser.com/questions/102086/how-to-build-initrd-without-dmraid-driver-on-ubuntu-9-10)

After a reboot, the array is now recovering nicely!

---


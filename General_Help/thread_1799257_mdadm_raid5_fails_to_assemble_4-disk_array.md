---
title: "mdadm raid5 fails to assemble 4-disk array"
date: 2011-07-07
forum: General Help
---

### Post by poscaman on 2011-07-07
Hello, 

after each reboot /dev/md0 loses /dev/sde, as you can see

**mdadm -D /dev/md0**

```
/dev/md0:
        Version : 0.90
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jul  5 10:21:41 2011
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
         Events : 0.28886

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       0        0        3      removed
```

when trying to stop array and start it over i get 

[B]mdadm --assemble -v --force /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
[/B]
```
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 4.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sde to /dev/md0 as 4
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives (out of 4) and 1 spare.
```

any ideas?

---

### Post by psusi on 2011-07-07
Instead of trying to force an assemble with an out of sync drive, you need to --re-add the failed drive to the array.

---

### Post by poscaman on 2011-07-07
> **psusi said:**
> Instead of trying to force an assemble with an out of sync drive, you need to --re-add the failed drive to the array.

When i try to re-add the failed drive, using 

```
mdadm /dev/md0 --add /dev/sde
```

drive is added, array starts rebuilding, and after some hours reports OK.

But, after **each** reboot, the situation gets as described above....

---

### Post by psusi on 2011-07-07
--re-add, not --add.

---

### Post by poscaman on 2011-07-07
> **psusi said:**
> --re-add, not --add.

Well, i've added /dev/sde to /dev/md0 using --re-add, array got synchronized, but after reboot /dev/sde was again removed from the array...

(as described in the first post)

---

### Post by psusi on 2011-07-07
After you --re-add and let it synchronize, post the results of mdadm -D /dev/md0 and mdadm -E /dev/sd[bcde]

---

### Post by poscaman on 2011-07-08
**mdadm -D /dev/md0**

```
/dev/md0:
        Version : 0.90
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul  8 12:47:41 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
         Events : 0.41694

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde

```



**mdadm -E /dev/sd[bcde] **

```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jul  8 12:47:47 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f41ab500 - correct
         Events : 41694

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jul  8 12:47:47 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f41ab512 - correct
         Events : 41694

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jul  8 12:47:47 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f41ab524 - correct
         Events : 41694

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jul  8 12:47:47 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f41ab536 - correct
         Events : 41694

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde

```

---

### Post by psusi on 2011-07-08
That looks good.  So when you reboot, it is degraded again?  What does mdadm -E /dev/sde show at that point?

Did you modify the system at all?  Maybe to try to make it boot in degraded mode instead of halting?  What release of Ubuntu is this?

---

### Post by poscaman on 2011-07-08
It's Debian Squeeze

**dpkg -l mdadm**
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
ii  mdadm                                                 3.1.4-1+8efb9d1                                       tool to administer Linux MD arrays (software RAID)
```

System was upgraded from lenny to squeeze.

OLD mdadm was (2.6.7.2-3) 


after reboot 

**dmesg**


```
    1.440363] sd 0:0:1:0: [sda] 156299375 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.440429] sd 0:0:1:0: [sda] Write Protect is off
[    1.440432] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.440459] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.440683]  sda:
[    1.442582] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.442646] sd 2:0:0:0: [sdb] Write Protect is off
[    1.442649] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.442677] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.442856]  sdb:
[    1.443310] sd 3:0:0:0: [sdd] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.443366] sd 3:0:0:0: [sdd] Write Protect is off
[    1.443369] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.443393] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.443570]  sdd: sda1 sda2 <
[    1.456891] sd 2:0:1:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.457505]  unknown partition table
[    1.457529] sd 2:0:1:0: [sdc] Write Protect is off
[    1.457534] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.457577] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.457793] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.457978]  sdc:
[    1.460733] sd 3:0:1:0: [sde] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.461387]  unknown partition table
[    1.461436] sd 3:0:1:0: [sde] Write Protect is off
[    1.461441] sd 3:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    1.461477] sd 3:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.461681]  sde: unknown partition table
[    1.475431] sd 2:0:1:0: [sdc] Attached SCSI disk
[    1.478797] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.479502]  unknown partition table
[    1.479970] sd 3:0:1:0: [sde] Attached SCSI disk
[    1.482182]  sda5 >
[    1.483360] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.496374] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    1.496378] Uniform CD-ROM driver Revision: 3.20
[    1.496512] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.501979] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.502028] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.502219] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.502278] sd 2:0:1:0: Attached scsi generic sg3 type 0
[    1.502324] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    1.502902] sd 3:0:1:0: Attached scsi generic sg5 type 0
[    1.861286] async_tx: api initialized (async)
[    1.862120] xor: automatically using best checksumming function: pIII_sse
[    1.880503]    pIII_sse  :  6518.000 MB/sec
[    1.880506] xor: using function: pIII_sse (6518.000 MB/sec)
[    1.948520] raid6: int32x1    735 MB/s
[    2.016550] raid6: int32x2    753 MB/s
[    2.084613] raid6: int32x4    547 MB/s
[    2.152519] raid6: int32x8    490 MB/s
[    2.220515] raid6: mmxx1     2368 MB/s
[    2.288510] raid6: mmxx2     2596 MB/s
[    2.356513] raid6: sse1x1    1589 MB/s
[    2.424530] raid6: sse1x2    1995 MB/s
[    2.492506] raid6: sse2x1    2976 MB/s
[    2.560509] raid6: sse2x2    3320 MB/s
[    2.560511] raid6: using algorithm sse2x2 (3320 MB/s)
[    2.571490] md: raid6 personality registered for level 6
[    2.571493] md: raid5 personality registered for level 5
[    2.571496] md: raid4 personality registered for level 4
[    2.593552] md: md0 stopped.
[    2.596105] md: bind<sdc>
[    2.596296] md: bind<sdd>
[    2.597649] md: bind<sdb>
[    2.601226] raid5: device sdb operational as raid disk 0
[    2.601230] raid5: device sdd operational as raid disk 2
[    2.601232] raid5: device sdc operational as raid disk 1
[    2.601681] raid5: allocated 4222kB for md0
[    2.605253] 0: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.605258] 2: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.605262] 1: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.605265] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
[    2.605319] RAID5 conf printout:
[    2.605321]  --- rd:4 wd:3
[    2.605325]  disk 0, o:1, dev:sdb
[    2.605327]  disk 1, o:1, dev:sdc
[    2.605329]  disk 2, o:1, dev:sdd
[    2.605370] md0: detected capacity change from 0 to 4500905459712
[    2.609893]  md0: unknown partition table

```

while 

**mdadm -E /dev/sd[bcde] **

```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  8 16:54:30 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f41aee98 - correct
         Events : 41700

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  8 16:54:30 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f41aeeaa - correct
         Events : 41700

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Jul  8 16:54:30 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : f41aeebc - correct
         Events : 41700

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sde:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 54e55d36:c3971e21:d484c166:6e86c3d7
  Creation Time : Thu Apr 30 23:48:58 2009
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jul  8 16:52:25 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f41aee90 - correct
         Events : 41696

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde

```

---

### Post by psusi on 2011-07-08
Looks like a bug in debian then.  It seems to be activating the array in degraded mode when the first 3 disks are detected, and then when it detects the 4th disk, it doesn't know what to do with it.

---

### Post by poscaman on 2011-07-09
Probably....


also in dmesg there are those lines

```
[    2.651711] [    1.968079] raid6: int32x1    736 MB/s
[    2.036002] raid6: int32x2    752 MB/s
[    2.104013] raid6: int32x4    546 MB/s
[    2.172009] raid6: int32x8    490 MB/s
[    2.240027] raid6: mmxx1     2367 MB/s
[    2.308007] raid6: mmxx2     2592 MB/s
[    2.376016] raid6: sse1x1    1589 MB/s
[    2.444009] raid6: sse1x2    1978 MB/s
[    2.512008] raid6: sse2x1    2979 MB/s
[    2.580005] raid6: sse2x2    3351 MB/s
[    2.580007] raid6: using algorithm sse2x2 (3351 MB/s)
[    2.590990] md: raid6 personality registered for level 6
[    2.590994] md: raid5 personality registered for level 5
[    2.590996] md: raid4 personality registered for level 4
[    2.645438] md: md0 stopped.
[    2.649789] md: bind<sdc>
[    2.650560] md: bind<sdd>
[B][    2.650889] md: bind<sde>
[    2.651668] md: bind<sdb>
[    2.651711] md: kicking non-fresh sde from array!
[    2.651718] md: unbind<sde>
[    2.656569] md: export_rdev(sde)[/B]
[    2.665084] raid5: device sdb operational as raid disk 0
[    2.665088] raid5: device sdd operational as raid disk 2
[    2.665091] raid5: device sdc operational as raid disk 1
[    2.665514] raid5: allocated 4222kB for md0
[    2.665563] 0: w=1 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.665567] 2: w=2 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.665571] 1: w=3 pa=0 pr=4 m=1 a=2 r=4 op1=0 op2=0
[    2.665574] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
[    2.665620] RAID5 conf printout:
[    2.665622]  --- rd:4 wd:3
[    2.665625]  disk 0, o:1, dev:sdb
[    2.665627]  disk 1, o:1, dev:sdc
[    2.665629]  disk 2, o:1, dev:sdd
[    2.665667] md0: detected capacity change from

```

do these say something?

---

### Post by psusi on 2011-07-09
Yep, that looks like what is going on.

---


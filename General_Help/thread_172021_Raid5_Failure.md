---
title: "Raid5 Failure"
date: 2006-05-07
forum: General Help
---

### Post by rdred on 2006-05-07
On boot I'm getting errors on /dev/sd0, here's an excerpt from /var/log/kern.log

```
May  7 19:06:43 localhost kernel: [4296553.204000] ata4: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
May  7 19:06:43 localhost kernel: [4296553.204000] ata4: status=0x25 { DeviceFault CorrectedError Error }
May  7 19:06:43 localhost kernel: [4296553.204000] SCSI error : <3 0 0 0> return code = 0x8000002
May  7 19:06:43 localhost kernel: [4296553.204000] sdd: Current: sense key: Hardware Error
May  7 19:06:43 localhost kernel: [4296553.204000]     Additional sense: No additional sense information
May  7 19:06:43 localhost kernel: [4296553.204000] end_request: I/O error, dev sdd, sector 0
May  7 19:06:43 localhost kernel: [4296553.204000] printk: 47056 messages suppressed.
May  7 19:06:43 localhost kernel: [4296553.204000] Buffer I/O error on device sdd, logical block 0
May  7 19:06:43 localhost kernel: [4296553.205000] Buffer I/O error on device md0, logical block 0
May  7 19:06:43 localhost kernel: [4296553.205000] Buffer I/O error on device md0, logical block 0
```

I would just replace the failed disk of this 4 disk array, however, mdadm --detail /dev/md0 is showing 2 disks in active sync, one failed, and one spare?  I assume /dev/sda wasn't in active sync when /dev/sdd failed.

```
mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Sat Dec  3 01:20:00 2005
     Raid Level : raid5
     Array Size : 879171840 (838.44 GiB 900.27 GB)
    Device Size : 293057280 (279.48 GiB 300.09 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 25 01:51:01 2006
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 636a193b:ce1f1cfc:86ebffd6:83ce7279
         Events : 0.2932031

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       0        0        -      removed

       4       8        0        -      spare   /dev/sda
       5       8       48        -      faulty   /dev/sdd
```

```
mdadm --examine /dev/md0
mdadm: Cannot read superblock on /dev/md0
```

My main concern at this point, if possible, is to get the data off the raid array.  I assume /dev/sda-sdc are all good and only /dev/sdd has failed.  I've been searching around for a while but I'm just not sure what I can do in this situation.  Any suggestions?

---

### Post by rdred on 2006-05-09
Anyone know a good forum or site to look at for help on this?

---


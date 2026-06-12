---
title: "Drive keeps failing out of software RAID?"
date: 2010-01-26
forum: General Help
---

### Post by tehfade on 2010-01-26
I have 4 1.5 TB Seagate drives configured in RAID 5 via mdadm on Karmic. It seems that after a while, one drive always drops out of the array. It's a brand new drive, and after a reboot, it will come back in and rebuild just fine, so somehow I doubt the drive is actually failing.

Any ideas what may be going on?

Here's a dmesg snip. The mounting that happens at the top is the mounting of the array, and as you can see, after a while, there is some kind of write failure. 

[70178.385356] EXT3 FS on md0, internal journal
[70178.385373] EXT3-fs: mounted filesystem with writeback data mode.
[95234.954141] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[95234.954160] ata5.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[95234.954162]          res 40/00:00:c6:66:a8/00:00:ae:00:00/e0 Emask 0x4 (timeout)
[95234.954168] ata5.00: status: { DRDY }
[95234.954176] ata5: hard resetting link
[95235.480375] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[95235.484422] ata5.00: configured for UDMA/133
[95235.484458] ata5: EH complete
[95235.499572] end_request: I/O error, dev sdd, sector 2930271935
[95235.499586] md: super_written gets error=-5, uptodate=0
[95235.499595] raid5: Disk failure on sdd1, disabling device.
[95235.499597] raid5: Operation continuing on 3 devices.
[95235.531943] md: recovery of RAID array md0
[95235.531948] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[95235.531952] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[95235.531960] md: using 128k window, over a total of 1465135872 blocks.
[95235.531963] md: resuming recovery of md0 from checkpoint.
[95235.531966] md: md0: recovery done.
[95235.576936] RAID5 conf printout:
[95235.576939]  --- rd:4 wd:3
[95235.576944]  disk 0, o:1, dev:sda1
[95235.576947]  disk 1, o:1, dev:sdc1
[95235.576950]  disk 2, o:0, dev:sdd1
[95235.576953]  disk 3, o:1, dev:sde1
[95235.588647] RAID5 conf printout:
[95235.588652]  --- rd:4 wd:3
[95235.588657]  disk 0, o:1, dev:sda1
[95235.588660]  disk 1, o:1, dev:sdc1
[95235.588663]  disk 2, o:0, dev:sdd1
[95235.588666]  disk 3, o:1, dev:sde1
[95235.622877] RAID5 conf printout:
[95235.622883]  --- rd:4 wd:3
[95235.622889]  disk 0, o:1, dev:sda1
[95235.622891]  disk 1, o:1, dev:sdc1
[95235.622894]  disk 3, o:1, dev:sde1

---

### Post by tehfade on 2010-01-26
Bump. Anybody?

---


---
title: "Filesystem failure on power-fail!"
date: 2010-06-11
forum: General Help
---

### Post by BillRebey on 2010-06-11
I'm running some power-fail tests with 9.04, and the results are disastrous.  

On a busy system with lots of disk I/O, it takes only a handful of times pulling the plug and restarting the system before I get the errors reported below (from /var/log/kern.log, and reported to the active console in real time).  The system is badly broken at this point.   (The errors repeat every few seconds)

Can these errors be corrected, and more importantly, how do I prevent them in the future?  I know some of you are about to respond with "don't do that" (i.e., get a UPS, do a proper shutdown, buy a solar panel, etc.).  That's not the issue, though...power failure is a reality of life, and the box should be bricked just because the power goes out.

This is not an isolated incident - I am testing with 6 PCs, and in a matter of a half an hour, I've got 2 of them in this condition.

**I could really use some help solidifying the EXT3 file system** to avoid these errors.  Any direction at all is greatly appreciated!

```
Jun 11 13:08:57 SAM-0126 kernel: [  363.641141] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 11 13:08:57 SAM-0126 kernel: [  363.658972] ata1.00: BMDMA stat 0x25
Jun 11 13:08:57 SAM-0126 kernel: [  363.676623] ata1.00: cmd c8/00:08:bf:80:b4/00:00:00:00:00/e9 tag 0 dma 4096 in
Jun 11 13:08:57 SAM-0126 kernel: [  363.676628]          res 51/40:05:c2:80:b4/00:00:00:00:00/e9 Emask 0x9 (media error)
Jun 11 13:08:57 SAM-0126 kernel: [  363.712141] ata1.00: status: { DRDY ERR }
Jun 11 13:08:57 SAM-0126 kernel: [  363.729857] ata1.00: error: { UNC }
Jun 11 13:08:57 SAM-0126 kernel: [  363.765378] ata1.00: configured for UDMA/100
Jun 11 13:08:57 SAM-0126 kernel: [  363.765475] ata1: EH complete

Jun 11 13:09:01 SAM-0126 kernel: [  367.841019] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 11 13:09:01 SAM-0126 kernel: [  367.859237] ata1.00: BMDMA stat 0x25
Jun 11 13:09:01 SAM-0126 kernel: [  367.877350] ata1.00: cmd c8/00:08:bf:80:b4/00:00:00:00:00/e9 tag 0 dma 4096 in
Jun 11 13:09:01 SAM-0126 kernel: [  367.877355]          res 51/40:05:c2:80:b4/00:00:00:00:00/e9 Emask 0x9 (media error)
Jun 11 13:09:01 SAM-0126 kernel: [  367.913851] ata1.00: status: { DRDY ERR }
Jun 11 13:09:01 SAM-0126 kernel: [  367.931993] ata1.00: error: { UNC }
Jun 11 13:09:01 SAM-0126 kernel: [  367.969316] ata1.00: configured for UDMA/100
Jun 11 13:09:01 SAM-0126 kernel: [  367.969368] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun 11 13:09:01 SAM-0126 kernel: [  367.969381] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 13:09:01 SAM-0126 kernel: [  367.969395] Descriptor sense data with sense descriptors (in hex):
Jun 11 13:09:01 SAM-0126 kernel: [  367.969403]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 13:09:01 SAM-0126 kernel: [  367.969429]         09 b4 80 c2 
Jun 11 13:09:01 SAM-0126 kernel: [  367.969440] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 13:09:01 SAM-0126 kernel: [  367.969456] end_request: I/O error, dev sda, sector 162824386
Jun 11 13:09:01 SAM-0126 kernel: [  367.987675] ata1: EH complete
Jun 11 13:09:01 SAM-0126 kernel: [  368.004180] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Jun 11 13:09:01 SAM-0126 kernel: [  368.004572] sd 0:0:0:0: [sda] Write Protect is off
Jun 11 13:09:01 SAM-0126 kernel: [  368.004582] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 11 13:09:01 SAM-0126 kernel: [  368.005948] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 13:09:01 SAM-0126 kernel: [  368.007475] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Jun 11 13:09:01 SAM-0126 kernel: [  368.007923] sd 0:0:0:0: [sda] Write Protect is off
Jun 11 13:09:01 SAM-0126 kernel: [  368.007937] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 11 13:09:01 SAM-0126 kernel: [  368.015038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

---

### Post by gzarkadas on 2010-06-11
Use the following additional mount options for the corresponding mount points in your /etc/fstab:
```
<existing options>,barrier=1,data=journal
```From the `man mount' documentation: If you need this (data=journal) on the root mount point (the /) file system, pass the mode to the kernel as boot parameter, e.g. `rootflags=data=journal'.

You should also consider using ext4 instead of ext3.

See for further info:
inside a terminal: `man mount', especially the filesystem-specific section
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---


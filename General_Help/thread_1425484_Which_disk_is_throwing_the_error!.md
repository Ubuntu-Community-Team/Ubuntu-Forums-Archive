---
title: "Which disk is throwing the error?!"
date: 2010-03-09
forum: General Help
---

### Post by OliW on 2010-03-09
I'm getting errors like this:

```
Mar  9 10:02:24 bert kernel: [ 5729.748509] ata1.00: qc timeout (cmd 0xa0)
Mar  9 10:02:24 bert kernel: [ 5729.776890] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar  9 10:02:24 bert kernel: [ 5729.776895] ata1.00: irq_stat 0x40000001
Mar  9 10:02:24 bert kernel: [ 5729.776898] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Mar  9 10:02:24 bert kernel: [ 5729.776909] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Mar  9 10:02:24 bert kernel: [ 5729.776910]          res 51/24:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
Mar  9 10:02:24 bert kernel: [ 5729.776914] ata1.00: status: { DRDY ERR }
Mar  9 10:02:24 bert kernel: [ 5729.776921] ata1: hard resetting link
Mar  9 10:02:24 bert kernel: [ 5730.138369] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 10:02:24 bert kernel: [ 5730.141925] ata1.00: configured for UDMA/100
Mar  9 10:02:24 bert kernel: [ 5730.181094] ata1: EH complete
```

They happen on a worryingly frequent period and I'm worried that one of my disks is about to kick the bucket. While all the data is relatively safe in one of two RAID arrays, I need to know which disk is about to blow up. I need to somehow map **ata1.00** to a /dev/sdX device.

From there I can look up the serial number and check the SATA power and data cable for faults.

But yes... I've got 7 disks and a few USB card readers:

```
oli@bert:~/Desktop$ sudo lshw -c disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7240S
       vendor: Optiarc
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom6
       logical name: /dev/cdrw6
       logical name: /dev/dvd6
       logical name: /dev/dvdrw6
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: OCZ-AGILITY
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: 1.42
       serial: J0Y818HZPIKBT4F2AJ89
       size: 59GiB (64GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a2bef995
  *-disk:0
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 0
       bus info: scsi@12:0.0.0
       logical name: /dev/sdb
       version: 1AG0
       serial: S1Y6J1MS607706
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007c632
  *-disk:1
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 1
       bus info: scsi@12:0.1.0
       logical name: /dev/sdc
       version: 1AG0
       serial: S1XWJ1KSC28370
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00068797
  *-disk:2
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 2
       bus info: scsi@13:0.0.0
       logical name: /dev/sdd
       version: 1AG0
       serial: S1Y6J1MS607705
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e1553
  *-disk:3
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 3
       bus info: scsi@13:0.1.0
       logical name: /dev/sde
       version: 1AG0
       serial: S1XWJ1KSC28219
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00017846
  *-disk:0
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 0
       bus info: scsi@14:0.0.0
       logical name: /dev/sdf
       version: 1AG0
       serial: S1XWJ1KSC28406
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a73f9
  *-disk:1
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 1
       bus info: scsi@15:0.0.0
       logical name: /dev/sdg
       version: 1AG0
       serial: S1XWJ1KSC28467
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00048f00
  *-disk
       description: SCSI Disk
       product: Stylus Storage
       vendor: EPSON
       physical id: 0.0.0
       bus info: scsi@20:0.0.0
       logical name: /dev/sdh
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdh
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@21:0.0.0
       logical name: /dev/sdi
```

Place your bets please!

It's entirely possible you don't have enough information to figure out what's happening. If there's anything else I can divine from my computer, let me know and I'll let you know.

---

### Post by dcstar on 2010-03-09
> **OliW said:**
> I'm getting errors like this:

```
Mar  9 10:02:24 bert kernel: [ 5729.748509] ata1.00: qc timeout (cmd 0xa0)
Mar  9 10:02:24 bert kernel: [ 5729.776890] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Mar  9 10:02:24 bert kernel: [ 5729.776895] ata1.00: irq_stat 0x40000001
Mar  9 10:02:24 bert kernel: [ 5729.776898] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Mar  9 10:02:24 bert kernel: [ 5729.776909] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Mar  9 10:02:24 bert kernel: [ 5729.776910]          res 51/24:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
Mar  9 10:02:24 bert kernel: [ 5729.776914] ata1.00: status: { DRDY ERR }
Mar  9 10:02:24 bert kernel: [ 5729.776921] ata1: hard resetting link
Mar  9 10:02:24 bert kernel: [ 5730.138369] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  9 10:02:24 bert kernel: [ 5730.141925] ata1.00: configured for UDMA/100
Mar  9 10:02:24 bert kernel: [ 5730.181094] ata1: EH complete
```
.........
It's entirely possible you don't have enough information to figure out what's happening. If there's anything else I can divine from my computer, let me know and I'll let you know.

In your syslog file there might be other entries at boot time that indicate what drive this is, have a look for that ata1 string.

---

### Post by OliW on 2010-03-10
> **dcstar said:**
> In your syslog file there might be other entries at boot time that indicate what drive this is, have a look for that ata1 string.

Genius. It's my DVD+RW!

```
08:26:53 bert kernel: [    2.168177] ata1.00: ATAPI: Optiarc DVD RW AD-7240S, 1.00, max UDMA/100
```

I guess there isn't that much to worry about. I'll swap out the power and data cable and hopefully the error will go.

---


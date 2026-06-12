---
title: "ata errors after fsck"
date: 2009-12-13
forum: General Help
---

### Post by ENOTTY on 2009-12-13
Hi, last night I got a bunch of ata errors and smartd told me I had bad sectors on my drive, and some files on my drive got corrupted.

So I rebooted and ran fsck. fsck found some errors and fsck fixed them. (fsck -y /dev/sda).

But I'm getting a lot of ata errors regarding bad sectors when reading a file, even after the fsck. I thought fsck was supposed to remap the filesystem to avoid bad sectors, so I'm wondering why this keeps occurring.

What should I do? (I have backups and I plan to get a new drive soon, but I'd like to continue using this drive for now.)

My syslog is filled with messages like this:
```

Dec 13 15:03:12 gamera kernel: [ 7500.823881] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Dec 13 15:03:12 gamera kernel: [ 7500.823884] ata1.00: irq_stat 0x40000008
Dec 13 15:03:12 gamera kernel: [ 7500.823888] ata1.00: cmd 60/00:00:50:e3:87/01:00:16:00:00/40 tag 0 ncq 131072 in
Dec 13 15:03:12 gamera kernel: [ 7500.823889]          res 51/40:a0:b0:e3:87/0f:00:16:00:00/40 Emask 0x409 (media error) <F>
Dec 13 15:03:12 gamera kernel: [ 7500.823891] ata1.00: status: { DRDY ERR }
Dec 13 15:03:12 gamera kernel: [ 7500.823892] ata1.00: error: { UNC }
Dec 13 15:03:12 gamera kernel: [ 7500.838886] ata1.00: configured for UDMA/133
Dec 13 15:03:22 gamera kernel: [ 7500.838894] ata1: EH complete
Dec 13 15:03:22 gamera kernel: [ 7500.838961] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
Dec 13 15:03:22 gamera kernel: [ 7500.838975] sd 0:0:0:0: [sda] Write Protect is off
Dec 13 15:03:22 gamera kernel: [ 7500.838977] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 13 15:03:22 gamera kernel: [ 7500.838996] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```Thanks

---


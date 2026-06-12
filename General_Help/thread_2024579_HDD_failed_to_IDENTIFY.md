---
title: "HDD failed to IDENTIFY"
date: 2012-07-13
forum: General Help
---

### Post by TonyB84 on 2012-07-13
I have an interesting problem where a single sata HDD isn't showing up in linux on boot up, but will show up if I unplug its sata cable and plug it back in.

I have 2 identical WD20EARX HDDs on an old AMD 2400+ PC running as a home server (ubuntu server 12.04).  The HDDs are connected to the onboard SATA controller - a SiI 3112.  I have a separate PATA HDD that linux boots from.

Initially both HDDs worked fine, I had set up a BTRFS filesytem on them in a raid1 configuration.  After messing around with some filesystem stuff, upgrading packages and a few power offs without shutting down this problem appeared.  Sorry I don't have details on exactly what was done immediately before the problem occurred.

Now when I boot up with both HDDs plugged in they are both detected by bios.  After booting into linux only one will appear when I run fdisk -l.

looking back through dmesg I have the following:

[    2.420058] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.609047] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x17 @ 1, addr 9e:7f:ed:3d:ef:5d
[    2.609064] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    7.468163] ata3.00: qc timeout (cmd 0xec)
[    7.468189] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[    7.788051] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   17.832031] ata3.00: qc timeout (cmd 0xec)
[   17.832040] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[   18.152046] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   48.196032] ata3.00: qc timeout (cmd 0xec)
[   48.196041] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[   48.516046] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   48.836047] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   48.844952] ata4.00: ATA-8: WDC WD20EARX-00PASB0, 51.0AB51, max UDMA/133
[   48.844963] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   48.852975] ata4.00: configured for UDMA/100
[   48.853244] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARX-00P 51.0 PQ: 0 ANSI: 5

if I unplug and plug in the affected drive's sata cable I get the following:

[  632.830001] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0xe frozen
[  632.830032] ata3: SError: { PHYRdyChg 10B8B }
[  632.830064] ata3: hard resetting link
[  633.552048] ata3: SATA link down (SStatus 0 SControl 310)
[  633.552075] ata3: EH complete
[  638.376793] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[  638.376826] ata3: SError: { PHYRdyChg }
[  638.376856] ata3: hard resetting link
[  639.100061] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  639.190425] ata3.00: ATA-8: WDC WD20EARX-00PASB0, 51.0AB51, max UDMA/133
[  639.190432] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[  639.625244] ata3.00: configured for UDMA/100
[  639.625262] ata3: EH complete
[  639.625501] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EARX-00P 51.0 PQ: 0 ANSI: 5
[  639.631166] sd 1:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[  639.631173] sd 1:0:0:0: [sdc] 4096-byte physical blocks
[  639.631282] sd 1:0:0:0: [sdc] Write Protect is off
[  639.631288] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[  639.631334] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  639.632118] sd 1:0:0:0: Attached scsi generic sg3 type 0
[  639.645115]  sdc: unknown partition table
[  639.645536] sd 1:0:0:0: [sdc] Attached SCSI disk

And the drive appears.

- I have tried swapping sata cables but the problem always follows this particular drive.
- I have tried booting up with just one, or just the other HDD connected and its always the same drive that isn't detected.
- I have tried the drive in another (windows 7) pc and it shows up.
- I have tried a low level format of the affected drive but the problem remains.

I'm left scratching my head as to what could possibly cause this problem, any ideas?

Thanks
Tony

---

### Post by Rexilion on 2012-07-14
Can you check you upgraded the kernel? Maybe you ran into a regression in the driver that handles your ATA disks.

---

### Post by TonyB84 on 2012-07-14
Kernel has certainly been upgraded since the problem showed itself.  Its possible the problem showed up after a kernel update.
Kernel is currently 3.2.0-24
I have tried an ubuntu 9.10 live cd(whatever kernel that uses) without success.

I would have originally installed the latest ubuntu server release as of about October 2011.  I'll see if I can get that kernel back in there.

---

### Post by TonyB84 on 2012-07-16
No luck with older kernels.  Found out linux keeps all the previous kernels I had installed, so tried booting the following versions from GRUB.
2.6.38-8 (the one I originally installed and had working)
3.0.0-20
3.2.0-24
and also 2.6.31-14 from a cd.

Any other ideas?

---

### Post by dino99 on 2012-07-16
BTRFS is still a work in progress; so you might know what you are doing  :confused:

---

### Post by TonyB84 on 2012-07-18
I doubt its a BTRFS issue
a) Its falling over trying to identify the HDD, before it has any idea whats on the disk.
b) Its still doing it after a low level format.

---

### Post by Rexilion on 2012-08-25
I guess the drive is dying and that Linux is not detecting it because of that. Windows might use another method for this which still works.

This might sound lame but it's the best explanation I can come up with.

Maybe try diagnosing it under Windows?

---


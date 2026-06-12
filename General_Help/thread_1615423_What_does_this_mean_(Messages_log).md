---
title: "What does this mean (Messages log)?"
date: 2010-11-07
forum: General Help
---

### Post by edward1978 on 2010-11-07
I have found it when I have been freezing on the time of the freeze the last 3 times it happened... I have to reboot to get out, even when the mouse pointer is the only thing frozen.

Nov  6 23:37:21 edward78-desktop kernel: [ 1198.000037] ata1: lost interrupt (Status 0x51)
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000540] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000552] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000590] ata1: soft resetting link
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.180246] ata1.00: configured for UDMA/33
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180028] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180034] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180055] ata1: soft resetting link
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.360256] ata1.00: configured for UDMA/33
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360038] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360044] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360048] ata1.00: limiting speed to UDMA/33:PIO3
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360069] ata1: soft resetting link
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.540236] ata1.00: configured for UDMA/33
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540031] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540037] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540040] ata1.00: disabled
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540067] ata1: soft resetting link
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.696070] ata1: EH complete

---

### Post by dcstar on 2010-11-07
> **edward1978 said:**
> I have found it when I have been freezing on the time of the freeze the last 3 times it happened... I have to reboot to get out, even when the mouse pointer is the only thing frozen.

Nov  6 23:37:21 edward78-desktop kernel: [ 1198.000037] ata1: lost interrupt (Status 0x51)
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000540] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000552] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.000590] ata1: soft resetting link
Nov  6 23:37:26 edward78-desktop kernel: [ 1203.180246] ata1.00: configured for UDMA/33
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180028] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180034] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.180055] ata1: soft resetting link
Nov  6 23:37:31 edward78-desktop kernel: [ 1208.360256] ata1.00: configured for UDMA/33
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360038] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360044] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360048] ata1.00: limiting speed to UDMA/33:PIO3
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.360069] ata1: soft resetting link
Nov  6 23:37:36 edward78-desktop kernel: [ 1213.540236] ata1.00: configured for UDMA/33
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540031] ata1.00: qc timeout (cmd 0xa0)
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540037] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540040] ata1.00: disabled
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.540067] ata1: soft resetting link
Nov  6 23:37:41 edward78-desktop kernel: [ 1218.696070] ata1: EH complete

It look like a hardware issue with one of the hard drives and/or CD/DVD.

It just could be a symptom of a bigger underlying problem but it doesn't look good and should not be there.

---

### Post by edward1978 on 2010-11-07
> **dcstar said:**
> It look like a hardware issue with one of the hard drives and/or CD/DVD.

It just could be a symptom of a bigger underlying problem but it doesn't look good and should not be there.

Hmmm... any way to find out more? I got the Western Digital Lifeguard util. for windows & booted to windows, ran it. The extended test turned out fine. ATA1 isn't my HDD if it is SATA right?

---

### Post by dino99 on 2010-11-07
run a fsck on next boot:

sudo shutdown now -R

---

### Post by P4man on 2010-11-07
> **dino99 said:**
> run a fsck on next boot:

sudo shutdown now -R

Whats that got to do with his problem ? This isnt a filesystem error.


@OP, try adding ```
all_generic_ide
``` to your kernel options. If you are not sure how, check my signature.

---

### Post by efflandt on 2010-11-07
ata1 is usually your main hard drive.  See which drive it is:

**dmesg | grep ata1**
```
[    1.127378] ata1: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4100 irq 45
[    1.480393] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.481700] ata1.00: ATA-8: ST31000528AS, CC45, max UDMA/133
[    1.481767] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.483287] ata1.00: configured for UDMA/133
```Do you have more than one hard drive, mixed SATA and PATA.  UDMA/33 sounds wrong unless it is an old system, old drive, or ATAPI (CD or DVD).  Even my old desktop from 2004 uses UDMA/100 for its PATA drive:

```
[    1.490772] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.671349] ata1.00: ATA-6: WDC WD2000BB-22DWA0, 15.05R15, max UDMA/100
[    1.671353] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.671379] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c0c0) ACPI=0x3f01f (17:900:0x11)
[    1.711301] ata1.00: configured for UDMA/100
```See what kind of drive it is and if it exists (maybe cabling is mixed up or connector not tight).  I had an issue with an old laptop when Linux kept polling a hot swap drive bay for non-existing floppy (which prevented suspend/hibernate).

---

### Post by dino99 on 2010-11-07
could be a bios settings corruption due to an too old bios battery

---

### Post by edward1978 on 2010-11-07
> **efflandt said:**
> ata1 is usually your main hard drive.  See which drive it is:

**dmesg | grep ata1**
```
[    1.127378] ata1: SATA max UDMA/133 abar m2048@0xf9ff4000 port 0xf9ff4100 irq 45
[    1.480393] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.481700] ata1.00: ATA-8: ST31000528AS, CC45, max UDMA/133
[    1.481767] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.483287] ata1.00: configured for UDMA/133
```Do you have more than one hard drive, mixed SATA and PATA.  UDMA/33 sounds wrong unless it is an old system, old drive, or ATAPI (CD or DVD).  Even my old desktop from 2004 uses UDMA/100 for its PATA drive:

```
[    1.490772] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.671349] ata1.00: ATA-6: WDC WD2000BB-22DWA0, 15.05R15, max UDMA/100
[    1.671353] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.671379] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c0c0) ACPI=0x3f01f (17:900:0x11)
[    1.711301] ata1.00: configured for UDMA/100
```See what kind of drive it is and if it exists (maybe cabling is mixed up or connector not tight).  I had an issue with an old laptop when Linux kept polling a hot swap drive bay for non-existing floppy (which prevented suspend/hibernate).

Only have 1 HDD, I have a IDE DVD drive, I am sure the cable is good, but I will check. So am I right thinking that the Western Digital Lifeguard test would have picked a lose cable up & reported errors? It didn't though... Is my Swap to small, I have 4 gig of mem.?

[IMG]http://img585.imageshack.us/img585/4846/screenshotg.png[/IMG]

---


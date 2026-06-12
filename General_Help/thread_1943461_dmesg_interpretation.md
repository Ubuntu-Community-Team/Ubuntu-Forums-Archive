---
title: "dmesg interpretation"
date: 2012-03-19
forum: General Help
---

### Post by yazmonium on 2012-03-19
can someone tell me what this means?  My cdrom drive has stopped mounting disks and I have a sinking feeling that it is a hardware problem.

[  123.449423] ata4: hard resetting link
[  123.776041] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  123.776080] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  124.262568] init: plymouth-stop pre-start process (2551) terminated with status 1
[  128.776046] ata4: hard resetting link
[  129.096040] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  129.096530] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB00, max UDMA/100
[  129.097234] ata4.00: configured for UDMA/100
[  134.096045] ata4.00: qc timeout (cmd 0xa0)
[  134.096051] ata4.00: TEST_UNIT_READY failed (err_mask=0x4)
[  134.096056] ata4.00: limiting speed to UDMA/100:PIO3
[  134.096060] ata4: hard resetting link
[  134.416050] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  134.416080] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  134.416083] ata4.00: revalidation failed (errno=-5)
[  134.416085] ata4.00: disabled
[  134.416095] ata4: exception Emask 0x10 SAct 0x0 SErr 0x1c00000 action 0x6 frozen t4
[  134.416097] ata4: irq_stat 0x08000000, interface fatal error
[  134.416100] ata4: SError: { Handshk LinkSeq TrStaTrns }
[  134.416104] ata4: hard resetting link
[  134.736049] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  134.736063] ata4: EH complete

---

### Post by SeijiSensei on 2012-03-19
Yes, it looks like a hardware failure.

If this is a laptop, you might try simply removing the device, blowing the dust out of the interior of the notebook, and reconnecting again.  If it's a desktop. check to make sure the cables are seated properly at both ends.

---

### Post by yazmonium on 2012-03-21
Aha!  The cables were loose.

---


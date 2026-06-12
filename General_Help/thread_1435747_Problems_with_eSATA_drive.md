---
title: "Problems with eSATA drive?"
date: 2010-03-21
forum: General Help
---

### Post by jdege on 2010-03-21
I'm running a clean install of 9.10 server, and I'm trying to do a backup to an eSATA drive.

The drive in question is a Western Digital WD1600AAJS - 160GB.

I'm attaching it through a VanTec NexStar hard drive dock.

It's an MSI 790GX-G65 mainboard.

The drive mounts fine, but with some regularity, during periods of heavy activity, Ubuntu simply loses track of it.  I've had it happen during mkfs, and I've had it happen while copying dump files.

In the logs, I'm seeing errors that look like hardware/driver problems.  First, a bunch of these:

Mar 21 20:15:06 home kernel: [  292.249357] ata6: soft resetting link
Mar 21 20:15:07 home kernel: [  292.474853] ata6.01: configured for UDMA/100
Mar 21 20:15:07 home kernel: [  292.474873] ata6: EH complete
Mar 21 20:15:07 home kernel: [  292.732532] ata6: soft resetting link
Mar 21 20:15:07 home kernel: [  292.964245] ata6.01: configured for UDMA/100
Mar 21 20:15:07 home kernel: [  292.964265] ata6: EH complete
Mar 21 20:15:14 home kernel: [  299.898488] ata6: soft resetting link
Mar 21 20:15:14 home kernel: [  300.124159] ata6.01: configured for UDMA/100
Mar 21 20:15:14 home kernel: [  300.124178] ata6: EH complete
Mar 21 20:15:28 home kernel: [  314.222360] ata6.01: limiting speed to UDMA/66:PIO4
Mar 21 20:15:28 home kernel: [  314.222444] ata6: soft resetting link

Then this:

Mar 21 20:18:04 home kernel: [  470.014983] ata6: EH complete
Mar 21 20:19:19 home kernel: [  544.990147] ata6: link is slow to respond, please be patient (ready=0)
Mar 21 20:19:24 home kernel: [  549.970156] ata6: device not ready (errno=-16), forcing hardreset
Mar 21 20:19:24 home kernel: [  549.970170] ata6: soft resetting link
Mar 21 20:19:30 home kernel: [  555.293970] ata6: link is slow to respond, please be patient (ready=0)
Mar 21 20:19:34 home kernel: [  560.033904] ata6: soft resetting link
Mar 21 20:19:40 home kernel: [  565.351401] ata6: link is slow to respond, please be patient (ready=0)
Mar 21 20:19:44 home kernel: [  570.090158] ata6: soft resetting link
Mar 21 20:19:50 home kernel: [  575.430156] ata6: link is slow to respond, please be patient (ready=0)
Mar 21 20:20:19 home kernel: [  605.130171] ata6: soft resetting link
Mar 21 20:20:24 home kernel: [  610.150189] ata6.01: disabled
Mar 21 20:20:24 home kernel: [  610.150208] ata6: EH complete
Mar 21 20:20:24 home kernel: [  610.150242] sd 5:0:1:0: [sdc] Unhandled error code
Mar 21 20:20:24 home kernel: [  610.150247] sd 5:0:1:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 20:20:24 home kernel: [  610.150270] lost page write due to I/O error on sdc5
Mar 21 20:20:24 home kernel: [  610.150287] lost page write due to I/O error on sdc5

Then thousands of these:

ar 21 20:20:24 home kernel: [  610.150486] sd 5:0:1:0: [sdc] Unhandled error code
Mar 21 20:20:24 home kernel: [  610.150490] sd 5:0:1:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 20:20:24 home kernel: [  610.150613] sd 5:0:1:0: [sdc] Unhandled error code
Mar 21 20:20:24 home kernel: [  610.150617] sd 5:0:1:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

Any ideas?

A bit of Googling resulted in a number of hits reprting similar problems, but nothing definitive, and nothing to indicate where the problem actually is.

Do I need a different dock?  A different drive?  To tweak some settings in the BIOS?

Help would be appreciated.

---


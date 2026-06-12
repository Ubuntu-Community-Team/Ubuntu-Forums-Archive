---
title: "Kernel/Hard drive bad sector/freezing issues"
date: 2010-12-23
forum: General Help
---

### Post by Norcalli on 2010-12-23
For some time now, my ubuntu distro (in Lucid and Maverick) has had a problem. I boot up and run for a while, then at some random time (usually while I'm watching a flash movie, which is cpu intensive) I look at the system monitor applet and see that there is high IOwait cpu usage (I think it is IOWait, it is the darker one). Then, if I don't act quickly and start killing (-s KILL) what I think the problem might be, I'll get a freeze and I can't do anything but hard reset. If I do manage to kill the responsible application, my home partition (mounted on sdc8 ) gets remounted as read only. If I go to tty1 (ctrl-alt-f1) I see that the kernel is throwing fits saying that there are errors at specific sectors, but when I do badblocks (and I've done it a dozen times), I get no bad blocks or sectors being read.

This has happened on multiple hard drives, which tells me that it is probably an OS specific issue or a motherboard issue. I thought that it had to do with ACPI, so I wrote "options libata noacpi=1" into "/etc/modprobe.d/options", but it didn't help (although maybe I did it wrong?). I finally got a log from when it happened and I dumped it.

```
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120050] ata5: EH in SWNCQ mode,QC:qc_active 0x3 sactive 0x3
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120054] ata5: SWNCQ:qc_active 0x1 defer_bits 0x2 last_issue_tag 0x0
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120055]   dhfis 0x1 dmafis 0x0 sdbfis 0x0
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120057] ata5: ATA_REG 0x40 ERR_REG 0x0
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120059] ata5: tag : dhfis dmafis sdbfis sacitve
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120061] ata5: tag 0x0: 1 0 0 1  
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120069] ata5.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120072] ata5.00: failed command: WRITE FPDMA QUEUED
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120076] ata5.00: cmd 61/08:00:bd:30:78/00:00:18:00:00/40 tag 0 ncq 4096 out
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120077]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120080] ata5.00: status: { DRDY }
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120082] ata5.00: failed command: WRITE FPDMA QUEUED
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120086] ata5.00: cmd 61/58:08:c5:30:78/00:00:18:00:00/40 tag 1 ncq 45056 out
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120087]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120089] ata5.00: status: { DRDY }
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120093] ata5: hard resetting link
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.120094] ata5: nv: skipping hardreset on occupied port
Dec 22 22:10:14 ashkan-ubuntu kernel: [21875.611759] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963771] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963776] sr 5:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963786] ata6.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963788]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963791] ata6.00: status: { DRDY }
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963795] ata6: hard resetting link
Dec 22 22:10:15 ashkan-ubuntu kernel: [21876.963797] ata6: nv: skipping hardreset on occupied port
Dec 22 22:10:16 ashkan-ubuntu kernel: [21877.450996] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 22:10:16 ashkan-ubuntu kernel: [21877.519182] ata6.00: configured for UDMA/100
Dec 22 22:10:19 ashkan-ubuntu kernel: [21880.630016] ata5.00: qc timeout (cmd 0x27)
Dec 22 22:10:19 ashkan-ubuntu kernel: [21880.630020] ata5.00: failed to read native max address (err_mask=0x4)
Dec 22 22:10:19 ashkan-ubuntu kernel: [21880.630022] ata5.00: revalidation failed (errno=-5)
Dec 22 22:10:19 ashkan-ubuntu kernel: [21880.630028] ata5: hard resetting link
Dec 22 22:10:19 ashkan-ubuntu kernel: [21880.630029] ata5: nv: skipping hardreset on occupied port
Dec 22 22:10:20 ashkan-ubuntu kernel: [21881.120019] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 22 22:10:21 ashkan-ubuntu kernel: [21882.512515] ata6.00: qc timeout (cmd 0xa0)
Dec 22 22:10:21 ashkan-ubuntu kernel: [21882.512519] ata6.00: TEST_UNIT_READY failed (err_mask=0x5)
Dec 22 22:10:21 ashkan-ubuntu kernel: [21882.512524] ata6: hard resetting link
Dec 22 22:10:21 ashkan-ubuntu kernel: [21882.512526] ata6: nv: skipping hardreset on occupied port
Dec 22 22:10:21 ashkan-ubuntu kernel: [21883.002524] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 22:10:22 ashkan-ubuntu kernel: [21883.062672] ata6.00: configured for UDMA/100
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061266] ata6.00: qc timeout (cmd 0xa0)
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061270] ata6.00: TEST_UNIT_READY failed (err_mask=0x5)
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061273] ata6: limiting SATA link speed to 1.5 Gbps
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061276] ata6.00: limiting speed to UDMA/100:PIO3
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061281] ata6: hard resetting link
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.061283] ata6: nv: skipping hardreset on occupied port
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.550023] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 22:10:27 ashkan-ubuntu kernel: [21888.620146] ata6.00: configured for UDMA/100
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140015] ata5.00: qc timeout (cmd 0x27)
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140018] ata5.00: failed to read native max address (err_mask=0x4)
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140021] ata5.00: revalidation failed (errno=-5)
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140024] ata5: limiting SATA link speed to 1.5 Gbps
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140028] ata5: hard resetting link
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.140030] ata5: nv: skipping hardreset on occupied port
Dec 22 22:10:30 ashkan-ubuntu kernel: [21891.630017] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 22 22:10:32 ashkan-ubuntu kernel: [21893.622515] ata6.00: qc timeout (cmd 0xa0)
Dec 22 22:10:32 ashkan-ubuntu kernel: [21893.622519] ata6.00: TEST_UNIT_READY failed (err_mask=0x5)
Dec 22 22:10:32 ashkan-ubuntu kernel: [21893.622522] ata6.00: disabled
Dec 22 22:10:32 ashkan-ubuntu kernel: [21893.622534] ata6: hard resetting link
Dec 22 22:10:33 ashkan-ubuntu kernel: [21894.542522] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 22 22:10:33 ashkan-ubuntu kernel: [21894.542540] ata6: EH complete
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652040] ata5.00: qc timeout (cmd 0x27)
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652044] ata5.00: failed to read native max address (err_mask=0x4)
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652046] ata5.00: revalidation failed (errno=-5)
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652049] ata5.00: disabled
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652055] ata5.00: device reported invalid CHS sector 0
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652059] ata5.00: device reported invalid CHS sector 0
Dec 22 22:10:40 ashkan-ubuntu kernel: [21901.652065] ata5: hard resetting link
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560017] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560032] ata5: EH complete
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560047] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560050] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560054] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 18 78 30 c5 00 00 58 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560063] end_request: I/O error, dev sdc, sector 410529989
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560082] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560084] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560087] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 18 78 30 bd 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560095] end_request: I/O error, dev sdc, sector 410529981
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560109] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560112] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560115] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 05 45 7f b5 00 00 38 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560123] end_request: I/O error, dev sdc, sector 88440757
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560126] Buffer I/O error on device sdc8, logical block 6464513
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560129] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560136] Buffer I/O error on device sdc8, logical block 6464514
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560138] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560142] Buffer I/O error on device sdc8, logical block 6464515
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560145] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560148] Buffer I/O error on device sdc8, logical block 6464516
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560150] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560153] Buffer I/O error on device sdc8, logical block 6464517
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560155] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560158] Buffer I/O error on device sdc8, logical block 6464518
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560160] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560163] Buffer I/O error on device sdc8, logical block 6464519
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560166] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560171] Aborting journal on device sdc8-8.
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560180] EXT4-fs error (device sdc8) in ext4_new_inode: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560191] EXT4-fs error (device sdc8) in ext4_reserve_inode_write: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560199] EXT4-fs error (device sdc8) in ext4_reserve_inode_write: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560204] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560206] EXT4-fs error (device sdc8) in ext4_reserve_inode_write: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560208] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560210] sd 4:0:0:0: [sdc] 
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560212] EXT4-fs error (device sdc8) in ext4_reserve_inode_write: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560214] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560216] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560224] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560226] sd 4:0:0:0: [sdc] 
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560227] Buffer I/O error on device sdc8, logical block 0
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560229] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560232] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560234] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 18 74 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560243] end_request: I/O error, dev sdc, sector 410279853
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560247] Buffer I/O error on device sdc8, logical block 46694400
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560249] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560255] JBD2: I/O error detected when updating journal superblock for sdc8-8.
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560263] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560265] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560268] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560275] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560278] Buffer I/O error on device sdc8, logical block 0
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560280] lost page write due to I/O error on sdc8
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560286] EXT4-fs error (device sdc8) in ext4_dirty_inode: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560288] EXT4-fs (sdc8): previous I/O error to superblock detected
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560293] EXT4-fs error (device sdc8) in ext4_create: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560297] end_request: I/O error, dev sdc, sector 0
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560308] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560309] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560312] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560318] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560337] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560339] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560342] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560348] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560353] EXT4-fs error (device sdc8) in ext4_dirty_inode: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560355] EXT4-fs (sdc8): previous I/O error to superblock detected
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560367] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560369] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560371] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560377] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560388] EXT4-fs error (device sdc8) in ext4_da_writepages: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560390] EXT4-fs (sdc8): 
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560392] EXT4-fs (sdc8): previous I/O error to superblock detected
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560395] EXT4-fs (sdc8): I/O error while writing superblock
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560399] I/O error while writing superblock
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560400] EXT4-fs error (device sdc8) in ext4_dirty_inode: Journal has aborted
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560403] 
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560404] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560406] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560409] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560421] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560439] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560441] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560443] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 02 30 5f ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560449] end_request: I/O error, dev sdc, sector 36724653
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560454] EXT4-fs error (device sdc8): ext4_journal_start_sb: Detected aborted journal
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560457] EXT4-fs (sdc8): Remounting filesystem read-only
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560459] EXT4-fs (sdc8): I/O error while writing superblock
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560461] EXT4-fs (sdc8): ext4_da_writepages: jbd2_start: 1024 pages, ino 2097161; err -30
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560515] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560518] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560521] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 06 4e dd ad 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560529] end_request: I/O error, dev sdc, sector 105831853
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560539] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560541] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560544] sd 4:0:0:0: [sdc] CDB: Write(10): 2a 00 05 45 8c c5 00 00 08 00
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560552] end_request: I/O error, dev sdc, sector 88444101
Dec 22 22:10:41 ashkan-ubuntu kernel: [21902.560558] JBD2: Detected IO errors while flushing file data on sdc8-8
Dec 22 22:11:09 ashkan-ubuntu kernel: [21930.646056] lo: Disabled Privacy Extensions
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088125] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088129] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088140] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 76 71 4d 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088149] end_request: I/O error, dev sdc, sector 91648333
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088174] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088176] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088179] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 76 71 4d 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.088187] end_request: I/O error, dev sdc, sector 91648333
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127442] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127446] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127450] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 64 ad 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127459] end_request: I/O error, dev sdc, sector 87123117
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127467] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573215: (comm gconfd-2) reading directory lblock 0
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127496] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127499] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127502] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 64 ad 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127511] end_request: I/O error, dev sdc, sector 87123117
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127518] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573215: (comm gconfd-2) reading directory lblock 0
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127547] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127549] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127553] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 64 b5 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127561] end_request: I/O error, dev sdc, sector 87123125
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127568] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573217: (comm gconfd-2) reading directory lblock 0
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127590] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127592] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127596] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 64 b5 00 00 08 00
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127604] end_request: I/O error, dev sdc, sector 87123125
Dec 22 22:11:16 ashkan-ubuntu kernel: [21937.127610] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573217: (comm gconfd-2) reading directory lblock 0
Dec 22 22:11:28 ashkan-ubuntu kernel: [21949.622074] lo: Disabled Privacy Extensions
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238286] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238289] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238292] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 44 2c f5 00 00 08 00
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238299] end_request: I/O error, dev sdc, sector 88354037
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238316] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238317] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238320] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 44 2c f5 00 00 08 00
Dec 22 22:12:07 ashkan-ubuntu kernel: [21988.238326] end_request: I/O error, dev sdc, sector 88354037
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603002] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603005] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603008] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 5d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603015] end_request: I/O error, dev sdc, sector 87122781
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603022] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573043: (comm gconfd-2) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603043] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603045] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603048] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 5d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603054] end_request: I/O error, dev sdc, sector 87122781
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603059] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573043: (comm gconfd-2) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603080] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603082] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603084] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 75 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603090] end_request: I/O error, dev sdc, sector 87122805
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603095] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573049: (comm gconfd-2) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603111] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603113] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603116] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 75 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603122] end_request: I/O error, dev sdc, sector 87122805
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.603126] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573049: (comm gconfd-2) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.607631] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.607634] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.607637] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 4d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.607643] end_request: I/O error, dev sdc, sector 87122765
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.607651] EXT4-fs error (device sdc8): ext4_find_entry: inode #1572990: (comm gedit) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611612] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611615] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611618] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 47 91 2d 00 00 18 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611624] end_request: I/O error, dev sdc, sector 88576301
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611640] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611642] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611645] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 47 91 2d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.611650] end_request: I/O error, dev sdc, sector 88576301
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.697761] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.697764] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.697767] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 4d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.697774] end_request: I/O error, dev sdc, sector 87122765
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.697786] EXT4-fs error (device sdc8): ext4_find_entry: inode #1572990: (comm gedit) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.771631] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.771634] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.771638] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 63 4d 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.771647] end_request: I/O error, dev sdc, sector 87122765
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.771674] EXT4-fs error (device sdc8): ext4_find_entry: inode #1572990: (comm gedit) reading directory lblock 0
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.905841] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.905844] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.905847] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.905854] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.911096] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.911098] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.911101] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.911108] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:33 ashkan-ubuntu kernel: [22194.911118] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573133: (comm gedit) reading directory lblock 0
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.524334] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.524337] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.524342] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.524350] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.531921] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.531924] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.531928] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.531937] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.531945] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573133: (comm gedit) reading directory lblock 0
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.533051] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.533054] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.533058] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.533066] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.533074] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573133: (comm gedit) reading directory lblock 0
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568812] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568816] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568820] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568829] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568855] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573133: (comm gedit) reading directory lblock 0
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568915] sd 4:0:0:0: [sdc] Unhandled error code
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568918] sd 4:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568921] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 05 31 68 15 00 00 08 00
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568930] end_request: I/O error, dev sdc, sector 87123989
Dec 22 22:15:50 ashkan-ubuntu kernel: [22211.568937] EXT4-fs error (device sdc8): ext4_find_entry: inode #1573133: (comm gedit) reading directory lblock 0

```

I'm also attaching my other logs from the past 2 days.

Relevant Hardware info:
-Motherboard: EVGA 790i Ultra SLI
-Video card: GTX 260
-Hard drives: G2 SSD 64 GB on /dev/sdb1 mounted as /, WD 400GB Caviar on /dev/sdc8 mounted as /home/
-CPU: Q9450
-Ram: Patriot 4GB DDR3
-Kernel: Linux 2.6.35-24-generic, Maverick Meerkat 10.10


I am at my wits end, I'll consider doing anything to fix this and if I can't fix it, I'll just switch to Windows, that's how desperate I am.

---

### Post by Norcalli on 2010-12-29
I don't know why, but the problem went away when I cleaned my computer and let it rest. Maybe it was a cpu overheating problem or an "over-working the computer" problem, or even something wrong with my base installation of Maverick. All I know is that I reformatted and things work for now.

On a side note, my installer failed while I was installing Maverick, yet the Maverick installation works perfectly... Maybe it failed while installing non-essential updates. Just thought I should share.

---

### Post by Norcalli on 2011-03-14
Months later, I still had the problem, but I believe I finally found a solution. I made it into a script. The problem I believe originates with Nvidia sata controllers, so if you have an nvidia motherboard and you get the random crashes, you could try this script which disables some of the hard drive functions and the drivers (write caching, hcq, acpi, and apic). I don't know if it is all neccessary, but I'd rather sacrifice performance for stability.

Note, if you use this script or have the same problem, can you please post so I can see if this works and to track the progress of this error.

---

### Post by JasperE on 2011-03-21
I'm affected by the same or at least a very similar problem, one of the HDD's stops working, giving I/O errors on $ ls command.

Used H/W:
- Asrock ALIVENF7G-HDREADY (nVidia nForce 630A chipset)
- Seagate ST3500630AS Barracuda 7200.10 SATA 3.0Gb/s 500-GB Hard Drive

Things I have tried and checked (error continues to persist):
- Replaced SATA cable
- Added boot option noapic

I hope your script might help me out! Implementing the other boot options, except for the disabling cache.

This is what /var/log/messages looks like.
```
Mar 21 03:31:13 srv01 kernel: [3662131.205316] ata2: hard resetting link
Mar 21 03:31:23 srv01 kernel: [3662141.241605] ata2: hard resetting link
Mar 21 03:31:33 srv01 kernel: [3662151.271237] ata2: hard resetting link
Mar 21 03:31:43 srv01 kernel: [3662161.890039] ata2: link is slow to respond, please be patient (ready=0)
Mar 21 03:32:08 srv01 kernel: [3662186.320993] ata2: limiting SATA link speed to 1.5 Gbps
Mar 21 03:32:08 srv01 kernel: [3662186.321003] ata2: hard resetting link
Mar 21 03:32:13 srv01 kernel: [3662191.571335] ata2.00: disabled
Mar 21 03:32:13 srv01 kernel: [3662191.571348] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571354] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571360] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571365] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571370] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571375] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571380] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571386] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571391] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571396] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571402] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571407] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571413] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571418] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571423] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571432] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571440] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571449] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571458] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571467] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571476] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571485] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571494] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571502] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571511] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571520] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571529] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571538] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571547] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571556] ata2.00: device reported invalid CHS sector 0
Mar 21 03:32:13 srv01 kernel: [3662191.571628] ata2: EH complete
Mar 21 03:32:13 srv01 kernel: [3662191.571717] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:13 srv01 kernel: [3662191.571722] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:13 srv01 kernel: [3662191.571730] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 2b a9 86 3f 00 04 00 00
Mar 21 03:32:13 srv01 kernel: [3662191.593269] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.603795] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.613847] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.623384] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.632724] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.641871] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.650709] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.659162] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.667336] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.675250] lost page write due to I/O error on sdb1
Mar 21 03:32:13 srv01 kernel: [3662191.675502] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:13 srv01 kernel: [3662191.675504] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:13 srv01 kernel: [3662191.675507] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 2b a9 82 3f 00 04 00 00
Mar 21 03:32:13 srv01 kernel: [3662191.683644] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:13 srv01 kernel: [3662191.683646] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:13 srv01 kernel: [3662191.683649] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 4a 4b db 97 00 02 98 00
[cut! above 3 lines are repeated many times]
Mar 21 03:32:14 srv01 kernel: [3662192.090496] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:14 srv01 kernel: [3662192.090498] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:14 srv01 kernel: [3662192.090501] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 00 03 76 cf 00 00 20 00
Mar 21 03:32:14 srv01 kernel: [3662192.096229] JBD2: Detected IO errors while flushing file data on sdb1-8
Mar 21 03:32:14 srv01 kernel: [3662192.101321] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:14 srv01 kernel: [3662192.101324] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:14 srv01 kernel: [3662192.101328] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 30 87 00 00 08 00
Mar 21 03:32:14 srv01 kernel: [3662192.106986] JBD2: Detected IO errors while flushing file data on sdb1-8
Mar 21 03:32:14 srv01 kernel: [3662192.489685] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:14 srv01 kernel: [3662192.489691] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:14 srv01 kernel: [3662192.489696] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 42 a5 80 b7 00 00 08 00
Mar 21 03:32:14 srv01 kernel: [3662192.511056] sd 1:0:0:0: [sdb] Unhandled error code
[cut! above 3 lines are repeated many times]
Mar 21 03:32:14 srv01 kernel: [3662192.702707] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:14 srv01 kernel: [3662192.702710] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 42 30 00 e7 00 00 58 00
Mar 21 03:32:14 srv01 kernel: [3662192.742198] unable to read inode block - inode=69403101, block=138805264
Mar 21 03:32:14 srv01 kernel: [3662192.742297] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 03:32:14 srv01 kernel: [3662192.742300] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 03:32:14 srv01 kernel: [3662192.742304] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 42 a7 93 47 00 00 08 00
Mar 21 03:32:14 srv01 kernel: [3662192.769604] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 18:17:49 srv01 kernel: [3715327.591431] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 18:17:49 srv01 kernel: [3715327.591440] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
Mar 21 18:17:49 srv01 kernel: [3715327.598822] __ratelimit: 18733 callbacks suppressed
Mar 21 18:17:49 srv01 kernel: [3715327.606101] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 18:17:49 srv01 kernel: [3715327.606110] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 18:17:49 srv01 kernel: [3715327.606117] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Mar 21 18:17:50 srv01 kernel: [3715328.274801] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 18:17:50 srv01 kernel: [3715328.274812] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 18:17:50 srv01 kernel: [3715328.274821] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Mar 21 18:17:51 srv01 kernel: [3715329.110600] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 18:17:51 srv01 kernel: [3715329.110610] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 18:17:51 srv01 kernel: [3715329.110619] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Mar 21 18:17:52 srv01 kernel: [3715330.884815] sd 1:0:0:0: [sdb] Unhandled error code
Mar 21 18:17:52 srv01 kernel: [3715330.884825] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Mar 21 18:17:52 srv01 kernel: [3715330.884834] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Mar 21 18:17:53 srv01 kernel: [3715331.974702] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar 21 18:17:53 srv01 kernel: [3715331.978050] SGI XFS Quota Management subsystem
Mar 21 18:17:54 srv01 kernel: [3715332.049857] JFS: nTxBlock = 7737, nTxLock = 61899
Mar 21 18:17:54 srv01 kernel: [3715332.189260] NTFS driver 2.1.29 [Flags: R/O MODULE].
Mar 21 18:17:54 srv01 kernel: [3715332.296927] QNX4 filesystem 0.2.3 registered.
Mar 21 18:17:54 srv01 kernel: [3715332.413660] Btrfs loaded
```

Edit: Another interesting thing is that SMARTctl long tests get aborted:```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%     20222         -
# 2  Offline             Aborted by host               00%     19189         -
```

---


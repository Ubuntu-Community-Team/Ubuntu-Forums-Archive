---
title: "Faulty USB drive?"
date: 2011-06-21
forum: General Help
---

### Post by mrmcgibby on 2011-06-21
I have a USB drive that I've formatted as ext4.  I'm manually mounting it and trying to use it as a backup drive.  It seems that after some period of time, something fails, and the system brings the device up again.  It will show up as a different device when it comes up again. At first I thought that the gnome automount stuff was messing with my drive, but I've had the same problem with my own mounts now.

Do I have a faulty drive or is there something else going on?  I've pasted the relevant dmesg output.

-------------

[ 6893.668245] usb 2-1.7: new high speed USB device using ehci_hcd and address 12
[ 6894.409692] scsi14 : usb-storage 2-1.7:1.0
[ 6896.474018] scsi 14:0:0:0: Direct-Access     WD       My Passport 0730 1012 PQ: 0 ANSI: 6
[ 6896.474767] scsi 14:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[ 6896.475671] sd 14:0:0:0: Attached scsi generic sg3 type 0
[ 6896.475897] ses 14:0:0:1: Attached Enclosure device
[ 6896.476058] ses 14:0:0:1: Attached scsi generic sg4 type 13
[ 6900.392313] sd 14:0:0:0: [sdc] 1465081856 512-byte logical blocks: (750 GB/698 GiB)
[ 6900.393155] sd 14:0:0:0: [sdc] Write Protect is off
[ 6900.393160] sd 14:0:0:0: [sdc] Mode Sense: 47 00 10 08
[ 6900.393165] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 6900.395734] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 6900.395742]  sdc: sdc1
[ 6900.418734] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 6900.418741] sd 14:0:0:0: [sdc] Attached SCSI disk
[ 6928.872222] EXT4-fs (sdc1): recovery complete
[ 6928.872962] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[ 6974.649975] lo: Disabled Privacy Extensions
[ 6986.856300] usb 2-1.7: reset high speed USB device using ehci_hcd and address 12
[ 7048.337524] usb 2-1.7: reset high speed USB device using ehci_hcd and address 12
[ 7063.384831] usb 2-1.7: device descriptor read/64, error -110
[ 7078.535481] usb 2-1.7: device descriptor read/64, error -110
[ 7078.710624] usb 2-1.7: reset high speed USB device using ehci_hcd and address 12
[ 7078.887387] sd 14:0:0:0: Device offlined - not ready after error recovery
[ 7078.887418] sd 14:0:0:0: [sdc] Unhandled error code
[ 7078.887425] sd 14:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 7078.887435] sd 14:0:0:0: [sdc] CDB: Write(10): 2a 00 27 bd 59 7f 00 00 f0 00
[ 7078.887463] end_request: I/O error, dev sdc, sector 666720639
[ 7078.887473] quiet_error: 20 callbacks suppressed
[ 7078.887480] Buffer I/O error on device sdc1, logical block 83340072
[ 7078.887488] lost page write due to I/O error on sdc1
[ 7078.887500] Buffer I/O error on device sdc1, logical block 83340073
[ 7078.887507] lost page write due to I/O error on sdc1
[ 7078.887516] Buffer I/O error on device sdc1, logical block 83340074
[ 7078.887522] lost page write due to I/O error on sdc1
[ 7078.887529] Buffer I/O error on device sdc1, logical block 83340075
[ 7078.887532] lost page write due to I/O error on sdc1
[ 7078.887540] usb 2-1.7: USB disconnect, address 12
[ 7078.887551] Buffer I/O error on device sdc1, logical block 83340076
[ 7078.887558] lost page write due to I/O error on sdc1
[ 7078.887565] Buffer I/O error on device sdc1, logical block 83340077
[ 7078.887572] lost page write due to I/O error on sdc1
[ 7078.887580] Buffer I/O error on device sdc1, logical block 83340078
[ 7078.887586] lost page write due to I/O error on sdc1
[ 7078.887593] Buffer I/O error on device sdc1, logical block 83340079
[ 7078.887600] lost page write due to I/O error on sdc1
[ 7078.887607] Buffer I/O error on device sdc1, logical block 83340080
[ 7078.887614] lost page write due to I/O error on sdc1
[ 7078.887623] Buffer I/O error on device sdc1, logical block 83340081
[ 7078.887629] lost page write due to I/O error on sdc1
[ 7078.897732] JBD2: Detected IO errors while flushing file data on sdc1-8
[ 7078.897767] end_request: I/O error, dev sdc, sector 730081839
[ 7078.897775] Aborting journal on device sdc1-8.
[ 7078.897797] JBD2: I/O error detected when updating journal superblock for sdc1-8.
[ 7078.897820] EXT4-fs (sdc1): delayed block allocation failed for inode 38535356 at logical offset 114688 with max blocks 448 with error -30
[ 7078.897829] EXT4-fs error (device sdc1): ext4_journal_start_sb: Detected aborted journal
[ 7078.897837] EXT4-fs (sdc1): Remounting filesystem read-only
[ 7078.897843] 
[ 7078.897846] EXT4-fs error (device sdc1) in ext4_da_write_end: IO failure
[ 7078.897853] This should not happen!!  Data will be lost
[ 7078.898147] EXT4-fs (sdc1): ext4_da_writepages: jbd2_start: 448 pages, ino 38535356; err -30
[ 7080.032479] usb 2-1.7: new high speed USB device using ehci_hcd and address 13
[ 7080.774669] scsi15 : usb-storage 2-1.7:1.0
[ 7081.771175] scsi 15:0:0:0: Direct-Access     WD       My Passport 0730 1012 PQ: 0 ANSI: 6
[ 7081.772007] scsi 15:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[ 7081.772867] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 7081.773028] ses 15:0:0:1: Attached Enclosure device
[ 7081.773143] ses 15:0:0:1: Attached scsi generic sg4 type 13
[ 7081.774146] sd 15:0:0:0: [sde] 1465081856 512-byte logical blocks: (750 GB/698 GiB)
[ 7081.775740] sd 15:0:0:0: [sde] Write Protect is off
[ 7081.775748] sd 15:0:0:0: [sde] Mode Sense: 47 00 10 08
[ 7081.775753] sd 15:0:0:0: [sde] Assuming drive cache: write through
[ 7081.778509] sd 15:0:0:0: [sde] Assuming drive cache: write through
[ 7081.778517]  sde: sde1
[ 7081.797195] sd 15:0:0:0: [sde] Assuming drive cache: write through
[ 7081.797202] sd 15:0:0:0: [sde] Attached SCSI disk

---


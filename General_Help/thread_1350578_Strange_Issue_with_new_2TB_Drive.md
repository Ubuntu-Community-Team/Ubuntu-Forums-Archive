---
title: "Strange Issue with new 2TB Drive?"
date: 2009-12-09
forum: General Help
---

### Post by PlatosGimp on 2009-12-09
I had an external Seagate 500 GB drive previously installed in a external drive case connected via eSATA to an Asus P5e3 motherboard. Inside the system are 2x500gb drives in a RAID1 and 2x300GB WD Raptors also in RAID1 both attached to a 3ware controller.

Running WIndows XP and Ubuntu 9.10.

After replacing the external 500gb drive with a new Seagate 2TB drive, and formating as NTFS under Windows, and rebooting, the drive does not show up under Ubuntu 9.10 and below are the relevant sections of DMESG.

Although there appear to be hardware errors showing, not sure how to interpret, the drive shows up just fine under Windows XP?

Any ideas/suggestions?



[    2.680170] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.680203] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.680227] sd 0:0:0:0: [sda] Write Protect is off
[    2.680228] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.680241] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.680314]  sda:


[    5.965425] ata1.00: exception Emask 0x10 SAct 0x2 SErr 0x780100 action 0x6
[    5.965427] ata1.00: irq_stat 0x08000000
[    5.965429] ata1: SError: { UnrecovData 10B8B Dispar BadCRC Handshk }
[    5.965432] ata1.00: cmd 60/f8:08:08:00:00/00:00:00:00:00/40 tag 1 ncq 126976 in
[    5.965433]          res 40/00:08:08:00:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[    5.965434] ata1.00: status: { DRDY }
[    5.965438] ata1: hard resetting link

[    6.310023] ata1: SATA link down (SStatus 0 SControl 300)
[    6.476451] ata1: hard resetting link


[   16.480005] ata1: softreset failed (device not ready)
[   16.480008] ata1: hard resetting link
[   26.490005] ata1: softreset failed (device not ready)
[   26.490007] ata1: hard resetting link
[   37.100006] ata1: link is slow to respond, please be patient (ready=0)
[   61.523748] ata1: softreset failed (device not ready)
[   61.523753] ata1: limiting SATA link speed to 1.5 Gbps
[   61.523754] ata1: hard resetting link
[   66.750005] ata1: softreset failed (device not ready)
[   66.750006] ata1: reset failed, giving up
[   66.750008] ata1.00: disabled
[   66.750018] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen t4
[   66.750019] ata1: irq_stat 0x00400040, connection status changed
[   66.750021] ata1: SError: { PHYRdyChg CommWake DevExch }
[   66.750025] ata1: hard resetting link
[   76.800005] ata1: softreset failed (device not ready)
[   76.800006] ata1: hard resetting link
[   86.850005] ata1: softreset failed (device not ready)
[   86.850007] ata1: hard resetting link
[   97.860005] ata1: link is slow to respond, please be patient (ready=0)
[  121.860006] ata1: softreset failed (device not ready)
[  121.860009] ata1: limiting SATA link speed to 1.5 Gbps
[  121.860011] ata1: hard resetting link
[  127.070007] ata1: softreset failed (device not ready)
[  127.070009] ata1: reset failed, giving up
[  127.070015] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  127.070018] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  127.070022] Descriptor sense data with sense descriptors (in hex):
[  127.070023]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[  127.070030]         00 00 00 08
[  127.070033] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  127.070035] end_request: I/O error, dev sda, sector 8
[  127.070038] Buffer I/O error on device sda, logical block 1
[  127.070042] Buffer I/O error on device sda, logical block 2
[  127.070044] Buffer I/O error on device sda, logical block 3
[  127.070046] Buffer I/O error on device sda, logical block 4
[  127.070048] Buffer I/O error on device sda, logical block 5
[  127.070049] Buffer I/O error on device sda, logical block 6
[  127.070051] Buffer I/O error on device sda, logical block 7
[  127.070053] Buffer I/O error on device sda, logical block 8
[  127.070055] Buffer I/O error on device sda, logical block 9
[  127.070056] Buffer I/O error on device sda, logical block 10
[  127.070073] ata1: EH complete
[  127.070077] ata1.00: detaching (SCSI 0:0:0:0)



More Complete DMESG List:


[    1.773798] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.773809] ata4.01: SATA link down (SStatus 0 SControl 300)
[    1.773818] ata4.01: link offline, clearing class 3 to NONE
[    1.773968] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.773978] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.773985] ata3.01: link offline, clearing class 3 to NONE
[    1.794067] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100
[    1.794186] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100
[    1.830332] ata3.00: configured for UDMA/100
[    1.830401] ata4.00: configured for UDMA/100
[    1.870350] usb 2-4.1: configuration #1 chosen from 1 choice
[    1.870460] hub 2-4.1:1.0: USB hub found
[    1.870568] hub 2-4.1:1.0: 4 ports detected
[    1.950076] usb 2-4.2: new high speed USB device using ehci_hcd and address 5
[    2.149869] usb 2-4.2: configuration #1 chosen from 1 choice
[    2.230084] usb 2-5.1: new high speed USB device using ehci_hcd and address 6
[    2.340371] usb 2-5.1: configuration #1 chosen from 1 choice
[    2.340493] hub 2-5.1:1.0: USB hub found
[    2.340587] hub 2-5.1:1.0: 4 ports detected
[    2.420096] usb 2-5.2: new full speed USB device using ehci_hcd and address 7
[    2.602647] usb 2-5.2: configuration #1 chosen from 1 choice
[    2.640019] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.652142] ata1.00: ATA-6: ST32000542AS, CC32, max UDMA/133
[    2.652145] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.665761] ata1.00: configured for UDMA/133
[    2.680079] scsi 0:0:0:0: Direct-Access     ATA      ST32000542AS     CC32 PQ: 0 ANSI: 5
[    2.680108] usb 2-4.1.1: new low speed USB device using ehci_hcd and address 8
[    2.680170] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.680203] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.680227] sd 0:0:0:0: [sda] Write Protect is off
[    2.680228] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.680241] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.680314]  sda:
[    2.681063] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    2.685470] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.685472] Uniform CD-ROM driver Revision: 3.20
[    2.685534] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.685567] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.686293] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    2.690790] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.690850] sr 3:0:0:0: Attached scsi CD-ROM sr1
[    2.690883] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    2.798899] usb 2-4.1.1: configuration #1 chosen from 1 choice
[    2.890116] usb 2-5.1.1: new high speed USB device using ehci_hcd and address 9
[    3.083030] usb 2-5.1.1: configuration #1 chosen from 1 choice
[    5.883429]  sda1
[    5.883576] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.883584] Freeing unused kernel memory: 660k freed
[    5.883697] Write protecting the kernel read-only data: 7580k
[    5.941982] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    5.941984] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    5.942685] 3ware 9000 Storage Controller device driver for Linux v2.26.02.012.
[    5.942860] 3w-9xxx 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.942865] 3w-9xxx 0000:05:00.0: setting latency timer to 64
[    5.945729] Floppy drive(s): fd0 is 1.44M
[    5.952102] ohci1394 0000:06:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    5.956850] e1000e 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.956882] e1000e 0000:03:00.0: setting latency timer to 64
[    5.957026]   alloc irq_desc for 29 on node 0
[    5.957027]   alloc kstat_irqs on node 0
[    5.957042] e1000e 0000:03:00.0: irq 29 for MSI/MSI-X
[    5.962048] Initializing USB Mass Storage driver...
[    5.962119] scsi9 : SCSI emulation for USB Mass Storage devices
[    5.962209] scsi10 : SCSI emulation for USB Mass Storage devices
[    5.962250] usbcore: registered new interface driver usb-storage
[    5.962252] USB Mass Storage support registered.
[    5.962299] usb-storage: device found at 9
[    5.962299] usb-storage: waiting for device to settle before scanning
[    5.963919] usb-storage: device found at 5
[    5.963920] usb-storage: waiting for device to settle before scanning
[    5.964532] FDC 0 is a post-1991 82077
[    5.965425] ata1.00: exception Emask 0x10 SAct 0x2 SErr 0x780100 action 0x6
[    5.965427] ata1.00: irq_stat 0x08000000
[    5.965429] ata1: SError: { UnrecovData 10B8B Dispar BadCRC Handshk }
[    5.965432] ata1.00: cmd 60/f8:08:08:00:00/00:00:00:00:00/40 tag 1 ncq 126976 in
[    5.965433]          res 40/00:08:08:00:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[    5.965434] ata1.00: status: { DRDY }
[    5.965438] ata1: hard resetting link
[    5.970694] usbcore: registered new interface driver hiddev
[    5.979107] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1.1/2-4.1.1:1.0/input/input4
[    5.979155] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.7-4.1.1/input0
[    5.979169] usbcore: registered new interface driver usbhid
[    5.979170] usbhid: v2.6:USB HID core driver
[    6.010030] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.010112] ohci1394 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    6.072029] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febfe000-febfe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.182841] 0000:03:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1b:21:32:1b:24
[    6.182843] 0000:03:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    6.182924] 0000:03:00.0: eth0: MAC: 1, PHY: 4, PBA No: d50854-003
[    6.182939] scsi8 : 3ware 9000 Storage Controller
[    6.182973] 3w-9xxx: scsi8: Found a 3ware 9000 Storage Controller at 0xfeaff000, IRQ: 16.
[    6.310023] ata1: SATA link down (SStatus 0 SControl 300)
[    6.476451] ata1: hard resetting link
[    6.540005] 3w-9xxx: scsi8: Firmware FE9X 3.08.00.016, BIOS BE9X 3.08.00.004, Ports: 4.
[    6.540338] scsi 8:0:0:0: Direct-Access     AMCC     9650SE-4LP DISK  3.08 PQ: 0 ANSI: 5
[    6.540888] scsi 8:0:1:0: Direct-Access     AMCC     9650SE-4LP DISK  3.08 PQ: 0 ANSI: 5
[    6.549337] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    6.549399] sd 8:0:0:0: [sdb] 976771120 512-byte logical blocks: (500 GB/465 GiB)
[    6.549417] sd 8:0:1:0: Attached scsi generic sg4 type 0
[    6.549772] sd 8:0:1:0: [sdc] 585916416 512-byte logical blocks: (299 GB/279 GiB)
[    6.550046] sd 8:0:0:0: [sdb] Write Protect is off
[    6.550048] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.550422] sd 8:0:1:0: [sdc] Write Protect is off
[    6.550424] sd 8:0:1:0: [sdc] Mode Sense: 23 00 00 00
[    6.550542] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[    6.550796] sd 8:0:1:0: [sdc] Write cache: enabled, read cache: disabled, doesn't support DPO or FUA
[    6.551898]  sdb:
[    6.552196]  sdc: sdc1
[    6.552919]  sdb1 sdb2 <
[    6.553732] sd 8:0:1:0: [sdc] Attached SCSI disk
[    6.566902]  sdb5 sdb6 sdb7 sdb8 sdb9 sdb10 sdb11 > sdb3
[    6.630180] sd 8:0:0:0: [sdb] Attached SCSI disk
[    7.340106] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00023c014100bf8c]
[    7.390121] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[001e8c00000429e1]
[   10.968122] usb-storage: device scan complete
[   10.968491] usb-storage: device scan complete
[   10.971866] scsi 9:0:0:0: Direct-Access     SMSC     223 U HS-CF      3.60 PQ: 0 ANSI: 0
[   10.972738] scsi 10:0:0:0: Direct-Access     Generic  Flash HS-CF      5.39 PQ: 0 ANSI: 0
[   10.975110] scsi 9:0:0:1: Direct-Access     SMSC     223 U HS-MS      3.60 PQ: 0 ANSI: 0
[   10.975735] scsi 10:0:0:1: Direct-Access     Generic  Flash HS-COMBO   5.39 PQ: 0 ANSI: 0
[   10.978236] scsi 9:0:0:2: Direct-Access     SMSC     223 U HS-SM      3.60 PQ: 0 ANSI: 0
[   10.981237] scsi 9:0:0:3: Direct-Access     SMSC     223 U HS-SD/MMC  3.60 PQ: 0 ANSI: 0
[   10.981585] sd 9:0:0:0: Attached scsi generic sg5 type 0
[   10.981660] sd 9:0:0:1: Attached scsi generic sg6 type 0
[   10.981716] sd 9:0:0:2: Attached scsi generic sg7 type 0
[   10.981775] sd 9:0:0:3: Attached scsi generic sg8 type 0
[   10.981857] sd 10:0:0:0: Attached scsi generic sg9 type 0
[   10.981921] sd 10:0:0:1: Attached scsi generic sg10 type 0
[   11.009982] sd 10:0:0:0: [sdh] Attached SCSI removable disk
[   11.014230] sd 10:0:0:1: [sdi] Attached SCSI removable disk
[   11.076487] sd 9:0:0:2: [sdf] Attached SCSI removable disk
[   11.079858] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[   11.083357] sd 9:0:0:3: [sdg] Attached SCSI removable disk
[   11.086982] sd 9:0:0:1: [sde] Attached SCSI removable disk
[   16.480005] ata1: softreset failed (device not ready)
[   16.480008] ata1: hard resetting link
[   26.490005] ata1: softreset failed (device not ready)
[   26.490007] ata1: hard resetting link
[   37.100006] ata1: link is slow to respond, please be patient (ready=0)
[   61.523748] ata1: softreset failed (device not ready)
[   61.523753] ata1: limiting SATA link speed to 1.5 Gbps
[   61.523754] ata1: hard resetting link
[   66.750005] ata1: softreset failed (device not ready)
[   66.750006] ata1: reset failed, giving up
[   66.750008] ata1.00: disabled
[   66.750018] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen t4
[   66.750019] ata1: irq_stat 0x00400040, connection status changed
[   66.750021] ata1: SError: { PHYRdyChg CommWake DevExch }
[   66.750025] ata1: hard resetting link
[   76.800005] ata1: softreset failed (device not ready)
[   76.800006] ata1: hard resetting link
[   86.850005] ata1: softreset failed (device not ready)
[   86.850007] ata1: hard resetting link
[   97.860005] ata1: link is slow to respond, please be patient (ready=0)
[  121.860006] ata1: softreset failed (device not ready)
[  121.860009] ata1: limiting SATA link speed to 1.5 Gbps
[  121.860011] ata1: hard resetting link
[  127.070007] ata1: softreset failed (device not ready)
[  127.070009] ata1: reset failed, giving up
[  127.070015] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  127.070018] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  127.070022] Descriptor sense data with sense descriptors (in hex):
[  127.070023]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
[  127.070030]         00 00 00 08
[  127.070033] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[  127.070035] end_request: I/O error, dev sda, sector 8
[  127.070038] Buffer I/O error on device sda, logical block 1
[  127.070042] Buffer I/O error on device sda, logical block 2
[  127.070044] Buffer I/O error on device sda, logical block 3
[  127.070046] Buffer I/O error on device sda, logical block 4
[  127.070048] Buffer I/O error on device sda, logical block 5
[  127.070049] Buffer I/O error on device sda, logical block 6
[  127.070051] Buffer I/O error on device sda, logical block 7
[  127.070053] Buffer I/O error on device sda, logical block 8
[  127.070055] Buffer I/O error on device sda, logical block 9
[  127.070056] Buffer I/O error on device sda, logical block 10
[  127.070073] ata1: EH complete
[  127.070077] ata1.00: detaching (SCSI 0:0:0:0)
[  127.070261] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  127.070276] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  127.070278] sd 0:0:0:0: [sda] Stopping disk
[  127.070283] sd 0:0:0:0: [sda] START_STOP FAILED
[  127.070284] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  127.912048] xor: automatically using best checksumming function: generic_sse
[  127.959995]    generic_sse: 14029.200 MB/sec
[  127.959997] xor: using function: generic_sse (14029.200 MB/sec)
[  127.961149] device-mapper: dm-raid45: initialized v0.2594b
[  128.185855] PM: Starting manual resume from disk
[  128.185857] PM: Resume from partition 8:27
[  128.185858] PM: Checking hibernation image.
[  128.186176] PM: Resume from disk failed.
[  128.203325] EXT4-fs (sdb9): barriers enabled
[  128.219704] kjournald2 starting: pid 518, dev sdb9:8, commit interval 5 seconds
[  128.219716] EXT4-fs (sdb9): delayed allocation enabled
[  128.219719] EXT4-fs: file extents enabled
[  128.222994] EXT4-fs: mballoc enabled
[  128.223003] EXT4-fs (sdb9): mounted filesystem with ordered data mode
[  129.944402] Adding 4000144k swap on /dev/sdb11.  Priority:-1 extents:1 across:4000144k
[  130.732765] udev: starting version 147
[  131.049438] udev: renamed network interface eth0 to eth1
[  131.117544] EXT4-fs (sdb9): internal journal on sdb9:8
[  131.565604] EDAC MC: Ver: 2.1.0 Oct 16 2009
[  131.583414] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[  131.725922] kjournald starting.  Commit interval 5 seconds

---


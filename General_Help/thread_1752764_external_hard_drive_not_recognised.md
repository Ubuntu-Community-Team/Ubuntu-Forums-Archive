---
title: "external hard drive not recognised"
date: 2011-05-08
forum: General Help
---

### Post by mashedbear on 2011-05-08
I have an 7 year old Amacom 60Gb USB external hard drive - which is currently not recognised on a windows XP system or Ubuntu 10.10. The drive appears to power up OK and has not been physically damaged.

I believe file system is corrupt after aborting a reformat of the drive on an XP system. I would like to reformat the drive - using Ubuntu - and do not need to recover any data on the disk.

Running lsusb the hard drive does not appear to be recognised:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04ce:0002 ScanLogic Corp. SL11R-IDE IDE Bridge
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04a9:1094 Canon, Inc. PIXMA iP3000x Printer
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The output of demsg (at least the bottom portion which seems to relate to USB) is:
> [   27.206780] usb 2-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   29.630049] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   34.911268] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   35.150005] eth0: no IPv6 routers present
[   40.200026] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   45.490016] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[ 1427.821269] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 1428.074155] scsi5 : usb-storage 1-6:1.0
[ 1429.070810] scsi 5:0:0:0: Direct-Access     JetFlash Transcend 2GB    8.07 PQ: 0 ANSI: 2
[ 1429.071494] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1429.074174] sd 5:0:0:0: [sdc] 3944448 512-byte logical blocks: (2.01 GB/1.88 GiB)
[ 1429.074811] sd 5:0:0:0: [sdc] Write Protect is off
[ 1429.074816] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1429.074819] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1429.076913] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1429.076920]  sdc: sdc1
[ 1430.580398] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1430.580403] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 1470.088803] usb 1-6: USB disconnect, address 5
[ 1470.097367] FAT: Directory bread(block 7728) failed
[ 1470.097388] FAT: Directory bread(block 7729) failed
[ 1470.099156] FAT: Directory bread(block 7728) failed
[ 1470.099171] FAT: Directory bread(block 7729) failed
[ 1470.100800] FAT: Directory bread(block 7728) failed
[ 1470.100810] FAT: Directory bread(block 7729) failed
[ 1470.100869] FAT: Directory bread(block 7728) failed
[ 1470.100878] FAT: Directory bread(block 7729) failed
[ 1470.100974] FAT: Directory bread(block 7728) failed
[ 1470.100982] FAT: Directory bread(block 7729) failed
[ 1470.101040] FAT: Directory bread(block 7728) failed
[ 1470.101048] FAT: Directory bread(block 7729) failed
[ 1470.101142] FAT: Directory bread(block 7728) failed
[ 1470.101151] FAT: Directory bread(block 7729) failed


The drive is not listed using fdisk and does not appear to be mounted in /media 

How can I 'detect' and mount this drive so that I can then format it?  

Thanks

---


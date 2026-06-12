---
title: "USB detection fails"
date: 2010-03-12
forum: General Help
---

### Post by banditen on 2010-03-12
Hi! I am new to this forum but have been using Ubuntu for several years and I like it a lot. Right now Karmic on AMD.

Just a few days ago the USB detection of flash and disk stopped working. I have used it a lot and there was never a problem. The icon appeared on the desktop when I inserted a flash or disk in a USB port,  and it was ready for use. Now nothing visible happens. I have of course tested with different flash memorys and different disks and in all ports, but nothing is working. But the USB mouse is working as usual, and in all ports. I follow the standard Ubuntu update and install everything that comes with it.

From the log I get this when a USB flash memory is inserted:

[ 2354.060028] usb 2-4: new high speed USB device using ehci_hcd and address 4
[ 2354.277600] usb 2-4: configuration #1 chosen from 1 choice
[ 2354.294619] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2354.298764] usb-storage: device found at 4
[ 2354.298771] usb-storage: waiting for device to settle before scanning
[ 2359.307270] usb-storage: device scan complete
[ 2359.309744] scsi 10:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[ 2359.310799] sd 10:0:0:0: Attached scsi generic sg4 type 0
[ 2359.328212] sd 10:0:0:0: [sdd] 503808 512-byte logical blocks: (257 MB/246 MiB)
[ 2359.329573] sd 10:0:0:0: [sdd] Write Protect is off
[ 2359.329580] sd 10:0:0:0: [sdd] Mode Sense: 0b 00 00 08
[ 2359.329585] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[ 2359.339572] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[ 2359.339581]  sdd: sdd1
[ 2359.352577] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[ 2359.352590] sd 10:0:0:0: [sdd] Attached SCSI removable disk

So, obviously something happens but no icon on the desktop, and nothing in /media (where it should appear, as I recall). 

I would much appreciate any help with this problem.

Regards, Banditen :confused:

---


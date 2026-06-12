---
title: "Usb 3 hub messes with usb drivers"
date: 2012-01-17
forum: General Help
---

### Post by image28 on 2012-01-17
When I plug in a usb 3 hub, external harddrives get splicing input output error when copying most files and disappear from the system. Tried with 3 hard drives, and 3 usb keys on both a usb 3 hub and a usb 2 hub, all disks are usb 2. if I unplug the usb 3 hub, the harddrives will work ( slowly ) on the usb 2.0 hub fine and on the usb 3 ports. They also work find on my media box and brothers windows laptop.

I'm using ubuntu 11.10 64 bit, fully updated. usb disks are a mix of fat32 and ntfs.
All drives check out fine in chkdsk in windows. I sent the last hub back to the store because of this error, and got one that many websites said had linux support.
It's the Unitek Y-3041 usb 3.0 4 port hub. Need it because my computer doesn't have many usb ports, and I normaly have 3 2tb harddrives plugged in at all times, and transfer files between them, so I usb 2.0 hub is too slow.

lsusb output after the crash:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 004: ID 1532:0101 Razer USA, Ltd Copperhead Mouse

Dmesg output:
[   61.432694] usb 8-1.2: new high speed USB device number 3 using xhci_hcd
[   61.450989] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[   61.451502] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[   61.451988] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[   61.452489] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
[   61.852995] usbcore: registered new interface driver uas
[   61.872876] Initializing USB Mass Storage driver...
[   61.873224] scsi4 : usb-storage 8-1.2:1.0
[   61.873418] usbcore: registered new interface driver usb-storage
[   61.873421] USB Mass Storage support registered.
[   62.873764] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Blade     8.02 PQ: 0 ANSI: 0 CCS
[   62.874061] scsi: killing requests for dead queue
[   62.874508] scsi: killing requests for dead queue
[   62.892301] scsi: killing requests for dead queue
[   62.897656] scsi: killing requests for dead queue
[   62.898377] scsi: killing requests for dead queue
[   62.901088] scsi: killing requests for dead queue
[   62.908684] scsi: killing requests for dead queue
[   62.909155] scsi: killing requests for dead queue
[   62.917210] sd 4:0:0:0: [sdb] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[   62.917400] sd 4:0:0:0: [sdb] Write Protect is off
[   62.917410] sd 4:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   62.917809] sd 4:0:0:0: [sdb] No Caching mode page present
[   62.917815] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   62.918966] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   62.923793] sd 4:0:0:0: [sdb] No Caching mode page present
[   62.923804] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   62.925977]  sdb: sdb1
[   62.927200] sd 4:0:0:0: [sdb] No Caching mode page present
[   62.927209] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   62.927215] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  161.840188] xhci_hcd 0000:01:00.0: xHCI host not responding to stop endpoint command.
[  161.840204] xhci_hcd 0000:01:00.0: Assuming host is dying, halting host.
[  161.840253] xhci_hcd 0000:01:00.0: HC died; cleaning up
[  161.840397] usb 8-1: USB disconnect, device number 2
[  161.840413] usb 8-1.2: USB disconnect, device number 3
[  161.840427] sd 4:0:0:0: Device offlined - not ready after error recovery
[  161.840460] sd 4:0:0:0: [sdb] Unhandled error code
[  161.840467] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[  161.840479] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 96 80 00 00 f0 00
[  161.840506] end_request: I/O error, dev sdb, sector 38528
[  161.840568] sd 4:0:0:0: rejecting I/O to offline device
[  161.840666] sd 4:0:0:0: [sdb] Unhandled error code
[  161.840674] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  161.840684] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 97 70 00 00 10 00
[  161.840707] end_request: I/O error, dev sdb, sector 38768
[  161.884522] scsi: killing requests for dead queue

------------------------------

---

### Post by image28 on 2012-01-19
compiled a new kernel 3.2.1
and loaded the xhci module with
"modprobe xhci_hcd link_quirk=1"

now I get the following error
 usb 8-1.2: reset high-speed USB device number 3 using xhci_hcd
[  169.110126] usb 8-1.2: device descriptor read/8, error -110
[  174.437975] usb 8-1.2: device descriptor read/8, error -110
[  175.753976] hub 8-1:1.0: cannot disable port 2 (err = -110)
[  176.961919] hub 8-1:1.0: cannot reset port 2 (err = -110)
[  178.169821] hub 8-1:1.0: cannot reset port 2 (err = -110)
[  179.382356] hub 8-1:1.0: cannot reset port 2 (err = -110)
[  180.590018] hub 8-1:1.0: cannot reset port 2 (err = -110)
[  181.805481] hub 8-1:1.0: cannot reset port 2 (err = -110)
[  181.805497] hub 8-1:1.0: Cannot enable port 2.  Maybe the USB cable is bad?

it's a usb key, so no cable, works fine on my usb 2 hub when the usb 3 hub isn't plugged in. Can try with my other disks, but I'm sure it will get the same error.

---

### Post by image28 on 2012-01-19
My system is a Zotac Zbox Nano Ad10+ , usb 3 ports work ok without the hub.

---

### Post by image28 on 2012-01-20
I get the error when I plug the hd's directly into the usb 3 ports as well, worked fine when I got the computer in December. Please tell me my usb 3 ports arn't damaged somehow. tried booting into ubuntu off a usb key on the usb 2 port, and it still got the error.

---


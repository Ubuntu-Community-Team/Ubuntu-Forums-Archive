---
title: "Can't read or mount USB flash drive"
date: 2010-06-01
forum: General Help
---

### Post by ezphilosophy on 2010-06-01
As the title suggests, I cannot mount my flash drive.  Fdisk doesn't detect the drive and from dmesg:
> [53769.784199] usb 1-3: new high speed USB device using ehci_hcd and address 12
[53769.920371] usb 1-3: configuration #1 chosen from 1 choice
[53769.923736] scsi10 : SCSI emulation for USB Mass Storage devices
[53769.926221] usb-storage: device found at 12
[53769.926237] usb-storage: waiting for device to settle before scanning
[53774.924740] usb-storage: device scan complete
[53774.926681] scsi 10:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 2
[53774.931295] sd 10:0:0:0: Attached scsi generic sg1 type 0
[53774.949996] sd 10:0:0:0: [sdb] READ CAPACITY failed
[53774.950007] sd 10:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[53774.950018] sd 10:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[53774.950029] sd 10:0:0:0: [sdb] Add. Sense: Invalid command operation code
[53774.950624] sd 10:0:0:0: [sdb] Write Protect is off
[53774.950636] sd 10:0:0:0: [sdb] Mode Sense: 16 24 09 51
[53774.950645] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[53774.959990] sd 10:0:0:0: [sdb] READ CAPACITY failed
[53774.960001] sd 10:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[53774.960012] sd 10:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[53774.960024] sd 10:0:0:0: [sdb] Add. Sense: Invalid command operation code
[53774.960606] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[53774.960623] sd 10:0:0:0: [sdb] Attached SCSI removable disk


What can I do to salvage this thing?

---


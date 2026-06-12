---
title: "USB storage issue on 9.04"
date: 2010-02-20
forum: General Help
---

### Post by sr_guy on 2010-02-20
Whenever I reboot I lose my 16gig USB thumb drive. It's formatted with a vfat partition. Here is the log from dmesg:

```

[    2.916478] Initializing USB Mass Storage driver...
[    2.932140] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.932322] usbcore: registered new interface driver usb-storage
[    2.932589] USB Mass Storage support registered.
[    2.933416] usb-storage: device found at 3
[    2.933419] usb-storage: waiting for device to settle before scanning
[    3.024026] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    3.052577] PM: Starting manual resume from disk
[    3.052580] PM: Resume from partition 8:5
[    3.052581] PM: Checking hibernation image.
[    3.052787] PM: Resume from disk failed.
[    3.093173] kjournald starting.  Commit interval 5 seconds
[    3.093189] EXT3-fs: mounted filesystem with ordered data mode.
[    3.157783] usb 1-8: configuration #1 chosen from 1 choice
[    3.158130] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.158299] usb-storage: device found at 4
[    3.158301] usb-storage: waiting for device to settle before scanning
[    3.476528] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    3.690100] usb 2-3: configuration #1 chosen from 1 choice

[    7.937211] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.937295] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    7.938055] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    7.938124] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    7.938985] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    7.939068] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    7.939800] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    7.939871] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    7.940855] sd 4:0:0:4: [sdf] Attached SCSI removable disk
[    7.940960] sd 4:0:0:4: Attached scsi generic sg6 type 0

```

---


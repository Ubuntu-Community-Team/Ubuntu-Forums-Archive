---
title: "Can't Mount USB Drive - RAID 5 Recovery"
date: 2009-08-23
forum: General Help
---

### Post by LonestarZ06 on 2009-08-23
Hello,

I recently had a failure of my Terastation HD-H1.0TGL/R5. However, I believe that my soft raid is in tact. I have been trying to use the instructions on the following URL:

[http://buffalo.nas-central.org/wiki/Terastation_Data_Recovery](http://buffalo.nas-central.org/wiki/Terastation_Data_Recovery)

However, mdadm can't go to work because my USB drives won't mount. Thus, the raid isn't recognized by mdadm. I would try to manually mount them, but since the drive isn't even seen by using "sudo fdisk -l" I don't think a manual mount would do anything. If anyone has any ideas how I could get these 4 drives to mount, it would be greatly appreciated.

Thanks,

Rob

---

### Post by LonestarZ06 on 2009-08-23
This is what it looks like as I attach the devices:

```
Aug 23 18:27:06 k2intsol99 kernel: [  390.601719] hub 1-1:1.0: USB hub found
Aug 23 18:27:06 k2intsol99 kernel: [  390.601788] hub 1-1:1.0: 4 ports detected
Aug 23 18:28:07 k2intsol99 kernel: [  451.711718] usb 1-1.1: new high speed USB device using ehci_hcd and address 7
Aug 23 18:28:07 k2intsol99 kernel: [  451.861289] usb 1-1.1: configuration #1 chosen from 1 choice
Aug 23 18:28:07 k2intsol99 kernel: [  451.896848] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 23 18:28:12 k2intsol99 kernel: [  456.900202] scsi 2:0:0:0: Direct-Access     WDC WD25 00BB-22RDA0      0K20 PQ: 0 ANSI: 2 CCS
Aug 23 18:28:12 k2intsol99 kernel: [  456.905422] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:28:12 k2intsol99 kernel: [  456.947602] sd 2:0:0:0: [sda] Write Protect is off
Aug 23 18:28:12 k2intsol99 kernel: [  456.948552] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:28:12 k2intsol99 kernel: [  456.953495] sd 2:0:0:0: [sda] Write Protect is off
Aug 23 18:28:12 k2intsol99 kernel: [  456.953521]  sda: sda1 sda2 sda3 sda4
Aug 23 18:28:12 k2intsol99 kernel: [  456.967415] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 23 18:28:12 k2intsol99 kernel: [  456.967549] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 23 18:29:00 k2intsol99 kernel: [  504.598148] usb 1-1.2: new high speed USB device using ehci_hcd and address 8
Aug 23 18:29:00 k2intsol99 kernel: [  504.723449] usb 1-1.2: configuration #1 chosen from 1 choice
Aug 23 18:29:00 k2intsol99 kernel: [  504.742581] scsi3 : SCSI emulation for USB Mass Storage devices
Aug 23 18:29:05 k2intsol99 kernel: [  509.745878] scsi 3:0:0:0: Direct-Access     WDC WD25 00BB-22RDA0      0K20 PQ: 0 ANSI: 2 CCS
Aug 23 18:29:05 k2intsol99 kernel: [  509.750986] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:29:05 k2intsol99 kernel: [  509.776520] sd 3:0:0:0: [sdb] Write Protect is off
Aug 23 18:29:05 k2intsol99 kernel: [  509.785106] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:29:05 k2intsol99 kernel: [  509.787015] sd 3:0:0:0: [sdb] Write Protect is off
Aug 23 18:29:05 k2intsol99 kernel: [  509.787041]  sdb: sdb1 sdb2 sdb3 sdb4
Aug 23 18:29:05 k2intsol99 kernel: [  509.801996] sd 3:0:0:0: [sdb] Attached SCSI disk
Aug 23 18:29:05 k2intsol99 kernel: [  509.802134] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 23 18:30:03 k2intsol99 kernel: [  567.829841] usb 1-1.4: new high speed USB device using ehci_hcd and address 9
Aug 23 18:30:03 k2intsol99 kernel: [  567.980043] usb 1-1.4: configuration #1 chosen from 1 choice
Aug 23 18:30:03 k2intsol99 kernel: [  568.017833] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 23 18:30:08 k2intsol99 kernel: [  573.021683] scsi 4:0:0:0: Direct-Access     WDC WD25 00BB-22RDA0      0K20 PQ: 0 ANSI: 2 CCS
Aug 23 18:30:08 k2intsol99 kernel: [  573.026409] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:30:08 k2intsol99 kernel: [  573.089748] sd 4:0:0:0: [sdc] Write Protect is off
Aug 23 18:30:08 k2intsol99 kernel: [  573.090665] sd 4:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:30:08 k2intsol99 kernel: [  573.092181] sd 4:0:0:0: [sdc] Write Protect is off
Aug 23 18:30:08 k2intsol99 kernel: [  573.092207]  sdc: sdc1 sdc2 sdc3 sdc4
Aug 23 18:30:08 k2intsol99 kernel: [  573.118255] sd 4:0:0:0: [sdc] Attached SCSI disk
Aug 23 18:30:08 k2intsol99 kernel: [  573.118393] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 23 18:30:45 k2intsol99 kernel: [  609.814739] usb 1-1.3: new high speed USB device using ehci_hcd and address 10
Aug 23 18:30:45 k2intsol99 kernel: [  609.939271] usb 1-1.3: configuration #1 chosen from 1 choice
Aug 23 18:30:45 k2intsol99 kernel: [  609.941008] scsi5 : SCSI emulation for USB Mass Storage devices
Aug 23 18:30:50 k2intsol99 kernel: [  614.955361] scsi 5:0:0:0: Direct-Access     WDC WD25 00BB-22RDA0      0K20 PQ: 0 ANSI: 2 CCS
Aug 23 18:30:50 k2intsol99 kernel: [  614.960444] sd 5:0:0:0: [sdd] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:30:50 k2intsol99 kernel: [  614.980070] sd 5:0:0:0: [sdd] Write Protect is off
Aug 23 18:30:50 k2intsol99 kernel: [  614.984205] sd 5:0:0:0: [sdd] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Aug 23 18:30:50 k2intsol99 kernel: [  614.984932] sd 5:0:0:0: [sdd] Write Protect is off
Aug 23 18:30:50 k2intsol99 kernel: [  614.984953]  sdd: sdd1 sdd2 sdd3 sdd4
Aug 23 18:30:50 k2intsol99 kernel: [  615.004648] sd 5:0:0:0: [sdd] Attached SCSI disk
Aug 23 18:30:50 k2intsol99 kernel: [  615.004803] sd 5:0:0:0: Attached scsi generic sg3 type 0
```

---

### Post by tgrimley on 2009-08-25
not sure how the raid is set up on the Terastation but it looks like you have 4 disks with 4 partitions each.  You don't need to mount the usb drives, just assemble the raid device and then mount that.  What's the configuration supposed to be?  Do you have 4 raid arrays?

---


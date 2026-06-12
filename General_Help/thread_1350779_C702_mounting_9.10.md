---
title: "C702 mounting 9.10"
date: 2009-12-09
forum: General Help
---

### Post by kDDs on 2009-12-09
Well the old work around for ubuntu versions up to and including 9.04 doesn't work, so what other fixes are there? I know its a **** phone, but it really should be supported out of the box...

Dmesg:

> [  584.493879] usb 1-3: USB disconnect, address 5
[  584.496516] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, f6a99080/36a99080 (bad dma)
[  584.496818] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-3, CDC Ethernet Device
[  589.331734] usb 1-3: new high speed USB device using ehci_hcd and address 6
[  589.475517] usb 1-3: configuration #3 chosen from 1 choice
[  589.483283] cdc_acm 1-3:3.1: ttyACM0: USB ACM device
[  589.489748] cdc_acm 1-3:3.3: ttyACM1: USB ACM device
[  589.510206] cdc_wdm 1-3:3.7: cdc-wdm0: USB WDM device
[  589.515897] usb0: register 'cdc_ether' at usb-0000:00:1d.7-3, CDC Ethernet Device, 02:80:37:17:03:00
[  590.336824] usb 1-3: USB disconnect, address 6
[  590.338834] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, f6a99100/36a99100 (bad dma)
[  590.339006] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-3, CDC Ethernet Device
[  622.272286] usb 1-3: new high speed USB device using ehci_hcd and address 7
[  622.801736] usb 1-3: configuration #2 chosen from 1 choice
[  622.807613] scsi3 : SCSI emulation for USB Mass Storage devices
[  622.808593] usb-storage: device found at 7
[  622.808608] usb-storage: waiting for device to settle before scanning
[  627.809960] usb-storage: device scan complete
[  627.811639] scsi 3:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
[  627.814163] scsi 3:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
[  627.816134] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  627.816565] sd 3:0:0:1: Attached scsi generic sg3 type 0
[  627.834842] sd 3:0:0:1: [sdd] 3995648 512-byte logical blocks: (2.04 GB/1.90 GiB)
[  627.835488] sd 3:0:0:0: [sdc] 368493 512-byte logical blocks: (188 MB/179 MiB)
[  627.841840] sd 3:0:0:1: [sdd] Test WP failed, assume Write Enabled
[  627.841852] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[  627.843926] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  627.843940] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  627.852181] sd 3:0:0:1: [sdd] Test WP failed, assume Write Enabled
[  627.852203] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[  627.852227]  sdd:
[  627.854356] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  627.854378] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  627.854400]  sdc: sdd1
[  627.868452]  sdc1
[  627.892713] sd 3:0:0:1: [sdd] Test WP failed, assume Write Enabled
[  627.892734] sd 3:0:0:1: [sdd] Assuming drive cache: write through
[  627.892757] sd 3:0:0:1: [sdd] Attached SCSI removable disk
[  627.895747] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  627.895768] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  627.895789] sd 3:0:0:0: [sdc] Attached SCSI removable disk


---

### Post by kDDs on 2009-12-21
Anyone?

---

### Post by daninch on 2010-01-04
Seriously, anyone? Need an answer for this myself...

---


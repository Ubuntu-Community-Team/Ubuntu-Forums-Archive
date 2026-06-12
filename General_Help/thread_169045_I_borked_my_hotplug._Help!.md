---
title: "I borked my hotplug. Help!"
date: 2006-05-01
forum: General Help
---

### Post by 0MG on 2006-05-01
Okay, I got a monkey virus.

Something I did killed my ability to hotplug my mp3 player. When I plug it in to the usb port, it doesn't mount automatically like it used to. Here is the relevant portion of dmesg if it helps.

```
[4310105.570000] usb 4-2: new high speed USB device using ehci_hcd and address 2
[4310106.041000] Initializing USB Mass Storage driver...
[4310106.050000] scsi0 : SCSI emulation for USB Mass Storage devices
[4310106.053000] usb-storage: device found at 2
[4310106.053000] usb-storage: waiting for device to settle before scanning
[4310106.053000] usbcore: registered new driver usb-storage
[4310106.053000] USB Mass Storage support registered.
[4310111.054000]   Vendor: TOSHIBA   Model: MK3006GAL         Rev: BY10
[4310111.054000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4310111.062000] usb-storage: device scan complete
[4310111.176000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4310111.176000] sda: assuming drive cache: write through
[4310111.179000] SCSI device sda: 58605120 512-byte hdwr sectors (30006 MB)
[4310111.179000] sda: assuming drive cache: write through
[4310111.179000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4310111.528000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
```


Where do I start? Appreciate any help you can give.

---

### Post by 0MG on 2006-05-01
btw, I don't really care about hotplug. It would be great if I could just mount the mp3 player. Any advice on editing fstab? Not sure what filesystem/options to choose.

---

### Post by sinkxdie on 2006-05-01
Did you ever see Road Trip when that nerd kids like
"haha, I boinked her guys" and everyone starts cracking up.
Oh well, about your problem, I don't know what to do this just reminded me of it.
Well anyway, 
*BUMP*

---


---
title: "ipod problem"
date: 2010-09-14
forum: General Help
---

### Post by KriZo on 2010-09-14
A couple of weeks ago Ubuntu 10.4 stopped working with my iPod 3G Nano. up until then when i plugged in my ipod it loaded in rythmbox and nautilus, but now nothing happens. GTK pod is able to read my ipod but can't write to it. What to do? I've run dmesg as a friend told me to do and heres is the output which I think is the useful part.

```
[15877.317382] wlan0: associated
[16608.029353] usb 2-2: new high speed USB device using ehci_hcd and address 3
[16608.162080] usb 2-2: configuration #1 chosen from 2 choices
[16608.269162] Initializing USB Mass Storage driver...
[16608.269492] scsi5 : SCSI emulation for USB Mass Storage devices
[16608.269817] usb-storage: device found at 3
[16608.269823] usb-storage: waiting for device to settle before scanning
[16608.269847] usbcore: registered new interface driver usb-storage
[16608.269854] USB Mass Storage support registered.
[16613.268777] usb-storage: device scan complete
[16613.284650] scsi 5:0:0:0: Direct-Access Apple iPod 1.62 PQ: 0 ANSI: 0
[16613.293850] sd 5:0:0:0: Attached scsi generic sg2 type 0
[16613.302756] sd 5:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[16613.303453] sd 5:0:0:0: [sdb] Write Protect is off
[16613.303461] sd 5:0:0:0: [sdb] Mode Sense: 68 00 00 08
[16613.303468] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[16613.305696] sd 5:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[16613.306724] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[16613.306731] sdb: sdb1
[16613.309437] sd 5:0:0:0: [sdb] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[16613.310055] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[16613.310060] sd 5:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by KriZo on 2010-09-19
Anybody?

---


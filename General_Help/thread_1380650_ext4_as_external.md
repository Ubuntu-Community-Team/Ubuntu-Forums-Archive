---
title: "ext4 as external"
date: 2010-01-13
forum: General Help
---

### Post by altonbr on 2010-01-13
I had a 1.5 TB hard drive as my /home drive in my desktop.

I sold my desktop and kept my 1.5 TB hard drive and put it in an external USB case.

Then I attached it to my Dell Inspiron Mini 9 and it failed to mount. I tried playing with the USB case and its connections only to find that Ubuntu /could/ read the external USB drive, it just can't read my ext4 drive.

This is me turning the external USB drive on and off again:

```
[  228.424907] usb 1-1: USB disconnect, address 4
[  438.177253] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  438.326195] usb 1-1: configuration #1 chosen from 1 choice
[  438.330850] scsi4 : SCSI emulation for USB Mass Storage devices
[  438.349736] usb-storage: device found at 5
[  438.349744] usb-storage: waiting for device to settle before scanning
[  443.352244] usb-storage: device scan complete
[  464.112193] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  474.372198] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  490.645580] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  490.937119] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  501.208169] usb 1-1: reset high speed USB device using ehci_hcd and address 5
[  501.357011] scsi 4:0:0:0: Device offlined - not ready after error recovery
[  503.920681] usb 1-1: USB disconnect, address 5
[  518.872217] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  519.017897] usb 1-1: configuration #1 chosen from 1 choice
[  519.031140] scsi5 : SCSI emulation for USB Mass Storage devices
[  519.033100] usb-storage: device found at 6
[  519.033115] usb-storage: waiting for device to settle before scanning

```

I tried using ```
sudo fdisk -l
``` both using my installed version of Ubuntu and a USB-Live version and also tried gparted in both and nothing can read it.

Is there anyway I can fix this without wiping my drive?

---

### Post by altonbr on 2010-01-14
bump

---

### Post by warfacegod on 2010-01-14
Is the drive encrypted?

---


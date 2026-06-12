---
title: "samsung freeform mass storage problem"
date: 2010-09-20
forum: General Help
---

### Post by djspork on 2010-09-20
the phone says it's connected ... ubuntu says it's connected but it just sits waiting for device to settle..
i was wondering if there was a way to force the scanning?
dmesg
```

[ 1249.469095] usb 3-2: USB disconnect, address 7
[ 1253.260032] usb 3-2: new full speed USB device using ohci_hcd and address 8
[ 1253.473042] usb 3-2: configuration #1 chosen from 1 choice
[ 1253.476015] cdc_acm 3-2:1.0: ttyACM0: USB ACM device
[ 1253.577611] usb 3-2: USB disconnect, address 8
[ 1255.124031] usb 3-2: new full speed USB device using ohci_hcd and address 9
[ 1255.340134] usb 3-2: configuration #1 chosen from 1 choice
[ 1255.349982] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1255.350084] usb-storage: device found at 9
[ 1255.350089] usb-storage: waiting for device to settle before scanning

```
lsusb
```

Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
any ideas why it's not mounting the micro sd card inside the phone?

---


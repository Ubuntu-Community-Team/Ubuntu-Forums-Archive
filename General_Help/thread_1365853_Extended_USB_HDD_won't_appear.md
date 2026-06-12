---
title: "Extended USB HDD won't appear"
date: 2009-12-27
forum: General Help
---

### Post by Mahngiel on 2009-12-27
Plugged it in via USB, but nothing.  Fdisk shows nothing either.  Any suggestions?

---

### Post by taurus on 2009-12-27
Is it fat32 or ntfs?  What happens when you look at the last few lines of dmesg, after you plugged in the drive?

```
dmesg | tail
```

---

### Post by Mahngiel on 2009-12-27
appears broken ;(
```

[ 5332.257514] scsi3 : SCSI emulation for USB Mass Storage devices
[ 5332.257751] usb-storage: device found at 7
[ 5332.257754] usb-storage: waiting for device to settle before scanning
[ 5337.256233] usb-storage: device scan complete
[ 5358.116061] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 5368.360050] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 5373.604054] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 5383.857820] usb 1-2: reset high speed USB device using ehci_hcd and address 7
[ 5383.995152] scsi 3:0:0:0: Device offlined - not ready after error recovery
[ 5464.399538] usb 1-4: USB disconnect, address 2

```

---

### Post by taurus on 2009-12-27
Is it a new drive, old drive, etc.?  Check to see the health of it if you have an access to a windows machine.

---

### Post by Mahngiel on 2009-12-27
It's fairly new.  Used it a few times and boxed it back up. Found it again and decided to use it.  But no windows access... well, at least i don't feel like installing Windows. :)

---

### Post by Mahngiel on 2009-12-27
So i blew some air into it and fiddled a bit. now my dmesg has changed:
```

[ 6748.690604] scsi4 : SCSI emulation for USB Mass Storage devices
[ 6748.693382] usb-storage: device found at 8
[ 6748.693387] usb-storage: waiting for device to settle before scanning
[ 6750.161092] usb 1-2: USB disconnect, address 8
[ 6752.536035] usb 1-2: new high speed USB device using ehci_hcd and address 9
[ 6752.669050] usb 1-2: configuration #1 chosen from 1 choice
[ 6752.682742] scsi5 : SCSI emulation for USB Mass Storage devices
[ 6752.687385] usb-storage: device found at 9
[ 6752.687398] usb-storage: waiting for device to settle before scanning
[ 6757.685257] usb-storage: device scan complete

```

---


---
title: "card wont read after failed format"
date: 2010-04-22
forum: General Help
---

### Post by cry8wolf9 on 2010-04-22
i tryed to format a mini sd card threw my hp officejet 7210 printer and while the format was going the power cut. now i cant get the card to read and i dont see it in the disk utility.


EDIT: heres the debug info for the card i think its the ;ast thing that shows up using dmesg
```

[  751.462676] usb 2-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1

```
and using lsusb this is what shows up
```

Bus 002 Device 003: ID 03f0:4111 Hewlett-Packard OfficeJet 7200 series
Bus 002 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b38:0010  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---


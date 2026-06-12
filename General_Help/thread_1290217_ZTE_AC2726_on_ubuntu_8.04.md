---
title: "ZTE AC2726 on ubuntu 8.04"
date: 2009-10-13
forum: General Help
---

### Post by Ang89 on 2009-10-13
Hi there,

I found several tutorials about how to setup ZTE AC2726 USB modem on ubuntu jaunty, but currently I'm using ubuntu hardy.
I plug my ZTE modem and check lsusb as the tutorials suggest. They say I should have the following line:
```
Bus 002 Device 009: ID 19d2:fff1
```
But sadly I'm not. The dmesg indicates that a USB device is detected, though.
```
[  741.321932] usb 5-2: new full speed USB device using uhci_hcd and address 2
[  741.485109] usb 5-2: configuration #1 chosen from 1 choice
[  935.828495] usb 5-2: USB disconnect, address 2
[ 1028.099229] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 1028.317290] usb 5-2: configuration #1 chosen from 1 choice
[ 1242.912456] usb 5-2: USB disconnect, address 3
[ 1253.802727] usb 5-2: new full speed USB device using uhci_hcd and address 4
[ 1253.960854] usb 5-2: configuration #1 chosen from 1 choice

```
Does anyone know how to fix this?

Thanks, 
Ang

---

### Post by P4man on 2009-10-13
Not sure if its fixable without upgrading to jaunty, but I guess you could try enabling the backports repository in software sources (update tab, select unsupported updates).

---

### Post by Ang89 on 2009-10-13
I plug my modem into another USB port and oddly it is detected :)

---


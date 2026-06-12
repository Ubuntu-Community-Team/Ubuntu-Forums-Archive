---
title: "Winpower and USB"
date: 2012-08-02
forum: General Help
---

### Post by oldfart101 on 2012-08-02
I have Winpower (UPS management software) connected via USB
the problem is - the software can't see the com port its connected to
outputs:-
```
LINUXPC ~ # dmesg|tail
[87142.468031] usb 3-1: device descriptor read/64, error -71
[87142.696040] usb 3-1: device descriptor read/64, error -71
[87142.912045] usb 3-1: new low speed USB device number 20 using uhci_hcd
[87143.328025] usb 3-1: device not accepting address 20, error -71
[87143.440035] usb 3-1: new low speed USB device number 21 using uhci_hcd
[87143.856022] usb 3-1: device not accepting address 21, error -71
[87143.856043] hub 3-0:1.0: unable to enumerate USB device on port 1
[87143.856065] usb 6-2: USB disconnect, device number 6
[87144.464033] usb 6-2: new low speed USB device number 7 using uhci_hcd
```and```
LINUXPC ~ # lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 007: ID 06da:0003 Phoenixtec Power Co., Ltd
```If I use /dev/ttyUSB6
or /dev/whatever/whatever
the software can't see the USB port
and when I re-boot, the device number changes
Any ideas??
p.s. tried a serial to usb converter, but needed it elsewhere ...
p.p.s its Bus 6 Device 7 (at the moment)

---


---
title: "TI-89 Titanium USB Cable connection"
date: 2010-10-17
forum: General Help
---

### Post by mechaxl on 2010-10-17
So I've got 10.10 installed, and I'm trying to hook up my Ti-89 Titanium to my computer. I've tried both the repo's tilp2, and installing it from source; neither one works. I think it's because for some reason my computer isn't seeing it. Here's my dump of lsusb:

> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 018: ID 19ff:0219 Dynex 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0461:4d75 Primax Electronics, Ltd 
Bus 005 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


It's plugged into the same set of plugs as my Dynex wireless mouse/keyboard combo, so I'm assuming that since the other Bus 006 slot is listed as empty, that my computer just isn't seeing it. Can anyone confirm/deny this?

---


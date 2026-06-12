---
title: "USB NanoStick ID 2013:024f not detected by 10.04"
date: 2011-07-14
forum: General Help
---

### Post by tobiz on 2011-07-14
My nanostick PCTV usb device ID 2013:024f is not being detected correctly (I suspect) by ubuntu 10.04 after I've built the cxd2820r driver for it.

On 2.6.32-32-generic, lsusb gives:
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0471:0330 Philips SPC 710NC PC Camera
Bus 002 Device 002: ID 0c16:0001 Gyration, Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 2013:024f
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Whereas on 2.6.38-8-generic (ubuntu 11.04) lsusb gives similar results but for ID 2013:024f says Unknown (Pinnacle?)

On the 11.04 system the cxd2820r driver installs ok and works whereas on the 10.04 it doesn't, it looks like it's not detected correctly as a usb device.  What's the problem and how's it fixed?

---


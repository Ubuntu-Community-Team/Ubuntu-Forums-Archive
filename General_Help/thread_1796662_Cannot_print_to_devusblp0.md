---
title: "Cannot print to /dev/usb/lp0"
date: 2011-07-04
forum: General Help
---

### Post by hgrimberg01 on 2011-07-04
I am trying to directly communicate with a receipt printer for a POS system over USB. It is a Star Micronics TSP100 series. The software pipes information to /dev/usb/lp0 to enable low-level ESC/POS  communcations(for stuff like cash drawers). I cannot get it to work according to the developers instructions. The permissions are correct(/dev/usb/lp0 is world writable). Others have reported successes with Epson printers in a similar setup. I tried using a virtual com port with same printer and same software under windows and everything works, so it is not the software or printer.

lsusb output:
Bus 002 Device 005: ID 0519:0003 Star Micronics Co., Ltd 
Bus 002 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:18ba Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

My setup:
Sony Vaio F12 Series laptop
Ubuntu 11.04 x64

Any suggestions?  Could it be something with udev?

---


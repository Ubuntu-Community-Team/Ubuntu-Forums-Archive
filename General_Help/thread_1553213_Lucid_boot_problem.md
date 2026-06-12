---
title: "Lucid boot problem"
date: 2010-08-14
forum: General Help
---

### Post by ndb on 2010-08-14
I'm new to Ubuntu and Linux so be patient :) My problem looks like this:

When I turn on my computer Ubuntu won't start, monitor goes to power save mode and lights for Caps and Scroll on the keyboard are blinking. When I add nomodeset in grub,  ubuntu starts but I have black screen with mouse pointer only (there is sound so I guess something is running I just cant see it)

And the most interesting thing is that when I boot my machine to windows then restart and boot to Ubuntu everything works fine. Till I turn off my computer, then I have to boot to windows and restart again. 

If i install ATI proprietary drivers Ubuntu wont work at all.

If it helps here is "hwinfo --gfx" output:
```
25: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_94c4
  Unique ID: VCu0.FFNSVSEEbl6
  Parent ID: gZD2._DRTE+iNX5E
  SysFS ID: /devices/pci0000:00/0000:00:0b.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV610 LE AGP [Radeon HD 2400 PRO AGP]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x94c4 "RV610 LE AGP [Radeon HD 2400 PRO AGP]"
  SubVendor: pci 0x1787 "Hightech Information System Ltd."
  SubDevice: pci 0x0028 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0xa800-0xa8ff (rw)
  Memory Range: 0xff4f0000-0xff4fffff (rw,non-prefetchable)
  Memory Range: 0xff4c0000-0xff4dffff (ro,prefetchable,disabled)
  IRQ: 18 (1553 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d000094C4sv00001787sd00000028bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (PCI bridge)
```My setup:
AMD A64 3000+  asus k8n-e 1GB ram Radeon hd2400 Ubuntu 10.04 Lucid

---


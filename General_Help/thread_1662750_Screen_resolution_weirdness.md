---
title: "Screen resolution weirdness"
date: 2011-01-08
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-01-08
So i setup ubuntu 10.04.1 for my neighbor
everything was fine on the live cd 
installed rebooted and the screen size went down to 800/600
installed updates and rebooted it was in a usable size
after another reboot it was back to 800/600 again 
the screen size on the live cd was 1280/1024
hwinfo for the vga
```
26: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1106_7205
  Unique ID: VCu0.2IfNDQxgdiF
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "VIA KM400/KN400/P4M800 [S3 UniChrome]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x7205 "KM400/KN400/P4M800 [S3 UniChrome]"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8118 
  Revision: 0x01
  Memory Range: 0xe4000000-0xe7ffffff (rw,prefetchable)
  Memory Range: 0xe8000000-0xe8ffffff (rw,non-prefetchable)
  Memory Range: 0xe9000000-0xe900ffff (ro,prefetchable,disabled)
  IRQ: 16 (no events)
  Module Alias: "pci:v00001106d00007205sv00001043sd00008118bc03sc00i00"
  Driver Info #0:
    Driver Status: viafb is not active
    Driver Activation Cmd: "modprobe viafb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

```
I think all i have to do is get to a tty mode and close gdm and generate an xorg.conf file and force the screen size with it
I have attached a full copy of the hwinfo output

---

### Post by realzippy on 2011-01-08
try this xorg.conf:
```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1280x1024"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```

---

### Post by pqwoerituytrueiwoq on 2011-01-08
thanks seems to be working so far
the boot logo seems to still get squished to the right of the screen still

---


---
title: "xorg.conf showing two graphic drivers"
date: 2006-05-09
forum: General Help
---

### Post by Xploit on 2006-05-09
So just installed the latest ati drivers, 8.24.8, according to the instructions posted at the ATi linux driver wiki.  Everything seems perfect.  I got my 1280*800 native resolution on my laptop.  The fireworks screen saver works how it is suppose to instead of being all slow like with the vesa drivers.  But xorg.conf shows two sections for my graphic device:

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        Option      "(null)"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

When I deleted the section with "vesa" in it then "X" would not start.  Is it okay how it is?

---


---
title: "Graphical Artifacts HD6770"
date: 2011-06-29
forum: General Help
---

### Post by silverforest on 2011-06-29
```
$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6700 Series 
OpenGL version string: 4.1.10834 Compatibility Profile Context
```Running latest Catalyst drivers.

Screenshots attached.

Something interesting I've noted is that I haven't noticed any glitches while having glxgears running in the background.

/etc/X11/xorg.conf:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```Any help at all is appreciated. These artifacts can make the screen unusable.

---


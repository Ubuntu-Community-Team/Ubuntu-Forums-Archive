---
title: "Proprietary ATI Video Driver Causes Desktop Tearing"
date: 2010-08-01
forum: General Help
---

### Post by LyeOnYou on 2010-08-01
I currently have FGLRX version 10.7 installed for my Radeon HD 4550 and have an annoying tearing problem.  This problem isn't new and I've been trying to get rid of it.  This occurs during video playback, window movements, and animations.  I've attached an image to show what's goin' on.

Here's my xorg.conf:

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
    Option        "Capabilities" "0x00000800"
    Option        "TexturedVideoSync" "on"
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

```

---


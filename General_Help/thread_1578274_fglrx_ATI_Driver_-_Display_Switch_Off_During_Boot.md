---
title: "fglrx ATI Driver - Display Switch Off During Boot"
date: 2010-09-20
forum: General Help
---

### Post by gallifrey on 2010-09-20
Hello all, 
            I have just installed an ATI Radeon HD 2600 Pro (AGP) in my tower. I installed the fglrx driver via Jockey, and ran 'aticonfig --initial', with no errors. 
Now, when I boot, it gets as far as the plymouth splash screen, and the display turns off, and the power light flashes on and off. If I boot in failsafe and use the backed up confguration, it works fine again. The monitor I am using is quite an old one - a 17" CRT with maximum resolution of 1152x864. I do not know the vendor. 

Here is the output of xorg.conf

> 
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
load "dri"
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
Any help would be gratefully appreciated :)

EDIT: fglrxinfo and glxinfo both give 'segmentation fault'. I have looked up this problem, but it seems o be a broad-spectrum thing.

---

### Post by gallifrey on 2010-09-21
I figured it out from /var/log/xorg.0.log.

The card was tying to set my monitor to a resolution of 1600x1200 during boot, which it couldn't handle. 

I just changed the resolution in xorg.conf.

---


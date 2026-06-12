---
title: "Changing Display to work on a 42' Screen"
date: 2010-01-14
forum: General Help
---

### Post by eino1953 on 2010-01-14
I would like to know if is script would work to change the display, and how do I get permission to change the file?

>  Section "Monitor"
Identifier "Monitor0"
VendorName "Sharp"
ModelName "LC-42SB45U"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection

---


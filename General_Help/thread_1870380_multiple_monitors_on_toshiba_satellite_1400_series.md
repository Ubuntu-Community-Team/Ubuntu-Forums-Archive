---
title: "multiple monitors on toshiba satellite 1400 series?"
date: 2011-10-27
forum: General Help
---

### Post by awesominator on 2011-10-27
i have a toshiba satellite 1400 series with a Trident microsystems CyberBlade XPAi1 graphics card and im trying to get multiple displays set up with my Samsung 940n monitor but ubuntu 10.04 only has "unknown monitor" listed in the monitors settings. clicking detect monitors doesn't work.

i want to have an extended screen. it seems to work when im using windows xp (running alongside).

here is my xorg.conf file that i had to create in order to get the screen resolutions that i needed. (ignore ***'s)
************************************************************************

Section "Device"
Identifier "Trident Microsystems CyberBlade XPAi1"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Generic Monitor"
Device "Trident Microsystems CyberBlade XPAi1"
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 32
Modes "1024x768"
EndSubSection
EndSection

************************************************************************
 is there a way to edit it so that it will work on extended displays? i cant install proprietry software as my Trident microsystems CyberBlade XPAi1 graphics card doesn't come up in "Hardware Drivers"

---


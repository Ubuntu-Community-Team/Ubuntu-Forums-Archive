---
title: "Adding Second Video Card for 3rd Display Jaunty"
date: 2010-01-27
forum: General Help
---

### Post by gotmonkey on 2010-01-27
In my system, I have a HD5870 that has 27in and 22in LCDs connected. There is also a HD4350 card in the system with a 22in LCD attached. According to ATI's driver page, both cards are supported by the Catalyst 9.12 driver. The system recognizes the additional card via $lspci.

Can anyone help me with adding that second card into my xorg.conf so I can use my third display? 

System Spec:
Intel DX58SO and Core i7-980X
6GB (3x2GB)Corsair XMS DDR3-1600
Seagate 250GB ES.2 SATA3G
XFX HD5870 (Primary 27in Display and Secondary 22in) 
XFX HD4350 (22in LCD for third display)

Thanks, 

gotmonkey


> Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 1680 0
Screen "amdcccle-Screen[2]-1" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
Option "Xinerama" "on"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Monitor"
Identifier "0-DFP3"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
Option "PreferredMode" "1680x1050"
Option "TargetRefresh" "60"
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false"
EndSection

Section "Monitor"
Identifier "0-DFP4"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
Option "PreferredMode" "2048x1152"
Option "TargetRefresh" "60"
Option "Position" "0 0"
Option "Rotate" "normal"
Option "Disable" "false"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option "Monitor-DFP4" "0-DFP4"
BusID "PCI:2:0:0"
EndSection

Section "Device"
Identifier "amdcccle-Device[2]-1"
Driver "fglrx"
Option "Monitor-DFP3" "0-DFP3"
BusID "PCI:2:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "Screen"
Identifier "amdcccle-Screen[2]-1"
Device "amdcccle-Device[2]-1"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection 

---


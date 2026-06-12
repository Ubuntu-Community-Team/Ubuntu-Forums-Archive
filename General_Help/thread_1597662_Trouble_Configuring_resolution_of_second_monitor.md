---
title: "Trouble: Configuring resolution of second monitor"
date: 2010-10-15
forum: General Help
---

### Post by Vinny_P on 2010-10-15
Hi all,

I have a laptop with an "ATI Technologies Inc Mobility Radeon HD 3400 Series" video device. I have trouble configuring the second VGA monitor attached to the laptop to 1024x768 resolution. It is always stuck on 2560x800.

My xorg.conf file is as follows:

```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Option "DefaultServerLayout"  "dualscreen"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Generic 1280x1024"
    ModeLine "1280x1024"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
    Option        "DPMS" "true"

EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Generic 1280x1024"
    SubSection "Display"
        Depth     24
        Modes   "1280x1024"
    EndSubSection
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    Monitor    "amdcccle-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1280x1024"
    EndSubSection
EndSection

```Any suggestions?

Thank you,
Vinny

---

### Post by Vinny_P on 2010-10-17
Pop-up :-)

---

### Post by lyall on 2010-10-17
try it link in the Ubuntu Documentation [https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
I did a search for second monitor

[https://help.ubuntu.com/community/XineramaHowTo]("https://help.ubuntu.com/community/XineramaHowTo")

hope this helps

good luck and have fun learning

---


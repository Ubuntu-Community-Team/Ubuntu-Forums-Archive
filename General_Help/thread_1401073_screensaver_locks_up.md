---
title: "screensaver locks up"
date: 2010-02-07
forum: General Help
---

### Post by coolclassic on 2010-02-07
I have an issue with my screensaver. Whilst leaving the computer unattended for a while the screensaver kicks in. The problem comes when I try to reactivate the screen, nothing happens the screen stays black unless I switch the monitor off and then on again. Unfortunately this does not work on every occasion and may need a few on/off to get a working screen. Whilst switching on the monitor the screen is active for a few seconds this can vary from 2-5 seconds. Then eventually after a few shots the only way to get an active screen is to reboot the computer.

Under normal activity with a period of inactivity a quick keyboard press or mouse activity activates the screen the problem only occurs when the computer is left for a longer period. 

Screen saver is disabled in system settings.

xorg.conf below for info:





Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "True"
    Option         "Xinerama" "0"
#other options can go here
    Option         "BlankTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
 EndSection





Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2234"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100 nForce 405"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


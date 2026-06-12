---
title: "Higher resolution for my Apple Cinema Display"
date: 2009-06-30
forum: General Help
---

### Post by noodle_soup on 2009-06-30
Hello all, I just got a 20" Apple Cinema Display that I have connected to my desktop PC via a Geforce 6200 video card, digital input. I am using Ubuntu 9.04. My problem is I want a higher screen resolution that the default maximum which is 1680x1050. I'm willing to bet it can go higher but I've never had much luck editing my xorg.conf files. Any help would be greatly appreciated. BTW I am using nvidia-settings. Here is my xorg.conf:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "hp P930"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 160.0
    Option "AllowDualLinkModes"
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
    BoardName      "GeForce 6200"
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
    Option         "metamodes" "1600x1200_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


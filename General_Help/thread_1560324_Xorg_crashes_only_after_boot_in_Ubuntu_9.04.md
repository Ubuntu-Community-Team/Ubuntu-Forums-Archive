---
title: "Xorg crashes only after boot in Ubuntu 9.04"
date: 2010-08-24
forum: General Help
---

### Post by wpy1505 on 2010-08-24
Hi,

I have a small issue of Xorg. Every time I boot the ubuntu 9.04, the X will crash immediately after it started. Then, it will start again and shows the login interface. It went well after the second login. I don't know what caused this since there is no error message in /var/log/Xorg.0.log and /var/log/gdm/*. 

Does anyone knows how should I inspect the issue, or know what was going on. Thanks in advance.

---

### Post by wpy1505 on 2010-08-24
Here is my xorg.conf:
[HTML]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load        "fbdev"
    Load        "glx"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/HTML]

---


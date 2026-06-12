---
title: "GeForce 9500ft on ubuntu 8.10(problems after restart)"
date: 2010-10-14
forum: General Help
---

### Post by marcusdufrane on 2010-10-14
Hello all,

I am having problems with getting the drivers to work for a geforce 9500gt.

To get started Im working with a fresh install of 8.10, and I have successfully installed the driver package for this card from nvidia's site, version 260.

The problem comes after I restart the computer. It fails to load. I am able to install the driver and start X and it works great. I can even restart x and it still works. but as soon as I restart the computer it doesn't load. I then need to reinstall the driver. I am curious if anyone has an idea of whats wrong here? I am wondering if it's a possible xorg.conf problem so I will post that below.


xorg.conf file

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    ModelName      "ELO ET1935L-8CWA"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by marcusdufrane on 2010-10-14
Anything guys? Im thinking that maybe theres a driver naming conflict or something.

---


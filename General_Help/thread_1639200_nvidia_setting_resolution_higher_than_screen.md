---
title: "nvidia setting resolution higher than screen"
date: 2010-12-06
forum: General Help
---

### Post by Cr0n_J0b on 2010-12-06
Hey, I have what I think is a pretty eay question.  I'm trying to set the screen resolution of my new 10.10 installation to 1920x1080.  The monitor only supports up to 1024x768, but i would like more area.  I've done this before but I forgot how i did it.  In the end the screen spilled off to the sides and when I ran my cursor over to that section it would disply it.  I have a feeling that i need to edit my xorg.conf file, but my nvidia drive has some new mode types and i figured I'd ask before making random changes.

below is my xorg.conf file.

UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Gateway FPD1540"
    HorizSync       31.0 - 60.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24

    EndSubSection
EndSection

---

### Post by lrgmmc on 2010-12-06
i think what you are looking for is overscan. it's in the nvidia-settings tool

---

### Post by Cr0n_J0b on 2010-12-12
Thanks, I didn't look all that hard in the tool, as I figured I needed to do something withthe config file.  It turns out that nVidia makes it dead easy.  You go into the tool under XServer Display Configuration, select the advanced button, and that will show a Panning box which is defaulted to the configured resolution.  I just changed that to 1920x1080 and hit apply...done.  no need to even log out which is cool.

---


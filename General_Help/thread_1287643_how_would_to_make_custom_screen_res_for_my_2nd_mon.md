---
title: "how would to make custom screen res for my 2nd monitor a LCD TV?"
date: 2009-10-10
forum: General Help
---

### Post by us12845 on 2009-10-10
how would i make custom screen res for my 2nd monitor a LCD TV?

First off I am brand new to linux/ubuntu so i really know nothing.  I have looked at over a dozen threads/websites and all I learned to do is save the changes I make in Nvidia X server and to back-up my xorg.conf.

I have a nvidia 8600M GT in my dell notebook.  I am connecting to a Samsung HD 46" LCD TV, via VGA to VGA.

As of right now my laptop LCD is displaying 1680x1050 @ 60 Hz, and my TV is displaying 1360x768 @ 60 Hz paning 1680x1050, I know a 16:10 and a 16:9 dont mix but it is the best I could do.  Additionally the only way I could get the laptop screen to be at the "normal" res was to have the Laptop display clone the CRT-0 or the TV.

So I just need to know how to run my external monitor (TV) at 1920x1080, this res is not in the list so i need to add it.

I did try and change the xorg.conf by hand to try and force the wanted res but it did not work 

Here is my xorg.conf  (DFP is my laptop screen and CRT-0 is my LCD TV)
------------------------------------------
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1360x768_60 @1680x1050 +0+0, DFP: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


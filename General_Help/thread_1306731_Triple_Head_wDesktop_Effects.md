---
title: "Triple Head w/Desktop Effects"
date: 2009-10-30
forum: General Help
---

### Post by ihod2009 on 2009-10-30
Hello folks, here goes.

I am currently using Ubuntu 9.10 on a machine that has two nVidia 8800GTS's and three 22" screens all running 1680x1050. I have been using this setup for a year now within KDE 3.5. I decided to move to Gnome because KDE 4 feels bloated to me and it does not like multiple monitors very well. I have never had any problems running this setup, which, by the way took me 3 weeks to figure out i put it together little by little. Its based on Xinerama and i get no compositing which for KDE is fine. Gnome on the other hand, being on my laptop is so sexy when compositing is enabled, i hate the bottom bar so im using AWN instead and i want to be able to do the same on my desktop.

I have been reading about xinerama being depreciated and xrandr being the new standard. I know nothing about xrandr and since my setup was fine for me, never cared to learn. Well, now is the time i wish to learn.

I would like to get all three screens working with compositing of some sort, weather it be compiz or the built-in solution which i think is probably more stable.

On another note, i am curious if TwinView can be tricked into running three screens. I noticed that it uses absolute positioning like xinerama does so i am tempted to add the third screen in as -1680.

Here is my current xorg.conf:
```
#openSUSE 11.1 X Configuration
#Built 1/25/2009
#Triple-Head w/Dual Video Cards


#Server Layout with center screen and subsequent ones on each side (right, left)
Section "ServerLayout"
    Identifier     "Layout0"
#Center Screen
    Screen      0  "Screen0" 1680 0
#Right Screen
    Screen      1  "Screen1" 3360 0
#Left Screen
    Screen      2  "Screen2" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
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
    Option         "Xinerama" "1"
    Option         "AutoAddDevices" "0"
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
    VendorName     "Hanns-G"
    ModelName      "HSD HW223"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1680x1050@75i" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync interlace
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Acer"
    ModelName      "X223W"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1680x1050@75i" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync interlace
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Hanns-G"
    ModelName      "HSD HW223"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    ModeLine       "1680x1050@75i" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync interlace
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0,NULL"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0,NULL"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0,NULL"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```I would really like to try out different xorg.conf files so if anyone has the kind of setup im looking for please let me know.

Thanks!

_Dan

---

### Post by ergosteur on 2009-12-14
Any luck with this? Just installed Ubuntu at work, running a 7900GS and a 7350LE with 3 19" displays.

---


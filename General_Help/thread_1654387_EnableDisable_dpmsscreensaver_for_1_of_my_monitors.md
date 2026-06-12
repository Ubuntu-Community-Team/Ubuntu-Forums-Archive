---
title: "Enable/Disable dpms/screensaver for 1 of my monitors ?"
date: 2010-12-28
forum: General Help
---

### Post by luceerose on 2010-12-28
I am using two monitors. A 23" LED Monitor & a 50" Plasma TV.
I basically want the TV to stay on all the time whilst the 23" monitor experiences either Power Saving or Screensaver.
So far I have found that both affect all monitors.
So, Is there a way to enable a Screensaver or Power Saving/dpms for only one monitor ?

I tried to set --Option "DPMS" "true"-- for Monitor0 & --Option "DPMS" "false"-- for Monitor1 in xorg file, but that didn't seem to make a difference to anything

Here's my xorg file:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "dri"
    Load           "GLcore"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "vmmouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option "ButtonMapping" "1 2 3"
    Option "ZAxisMapping" "4 5"
    Option "YAxisMapping" "6 7"
    Option "Resolution" "1600"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "E2340"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "LG"
    ModelName      "50PG60"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS" "false"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1920x1080_60 +0+0"
    Option         "AddARGBGLXVisuals" "true"
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
    Option         "metamodes" "DFP-1: 1920x1080_60 +0+0"
    Option         "AddARGBGLXVisuals" "true"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
What can I do ?

---

### Post by davidmohammed on 2010-12-28
try forcing one of your monitors to switch off

I think the syntax is something like

sleep 1 && xset -display <x> dpms force off

where <x> is the display number

---

### Post by luceerose on 2010-12-28
After a lot of fiddling around to get the 'display' parameter <:x.x> right, I managed to get the following commands to work;
```
sleep 1 && xset -display :0.0 dpms force off
sleep 1 && xset -display :0.1 dpms force off
```
Both of those gave me the same result. In both cases TWO monitors turned off, not just one.

P.S.
I'm positive I have the right display designations, now.
```
env | grep DISPLAY
```
gives me the following output, on Screen0 ;
```
DISPLAY=:0.0
```
&
on Screen1 ;
```
DISPLAY=:0.1
```

---

### Post by davidmohammed on 2010-12-28
ok - well done on finding the correct syntax.

The reason that both screens turn off is because both of your screens are connected to the same display - display 0

Somehow you need to have two displays running - each with one screen.

What is your setup?  I presume you've got two graphics cards - each with one screen connected?  In that case you should have two displays - display 0:0 and display 1:0

I think nvidia cards can do something similar - display 1:0 would be - for example - the laptop/internal screen, whereas display 0:0 would be the external VGA output.  I think you do this using nvidia settings making sure each display is independent, not a clone or possible an extension of the first.

---


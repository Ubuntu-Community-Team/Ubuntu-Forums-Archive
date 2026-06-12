---
title: "adding a second mouse device"
date: 2009-12-27
forum: General Help
---

### Post by Groundswell on 2009-12-27
is it possible to have 2 pointing devices under gnome?

i have an saitek x52 joystick system which has one of those old school mouse nubs, that little rubber nipple... hehe... nipple. :redface:  and i'de like it to also be able to control the mouse.

if i do
cat /dev/#whatever it was, can't remember now
it does detect input from it, but currently when in game (il-2) it interprets it as a x-axis movement as if i pulled the joystick to the left side.

the reasoning behind this is that when playing il-2 the mouse acts as a looking device, so having this extra mouse on the throttle makes easy quick and precise looking possible instead of using the hat switch.

any ideas or input from the general ubuntu mob would be greatly greatly appreciated.

---

### Post by bodhi.zazen on 2009-12-27
depends on the device.

See if this helps :

[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)

---

### Post by Groundswell on 2009-12-27
> **bodhi.zazen said:**
> depends on the device.

See if this helps :

[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)


apparently this package is included now? i tried adding the device to my xorg.conf but no difference. I've tried that in the past but figured i'de give it another go to no avail.

---

### Post by Groundswell on 2009-12-27
bump, here's my xorg

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Mouse2"
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
    Identifier "mouse2"
    Driver "mouse"
    Option "Device" "/dev/input/event6"
    Option "Protocol" "auto"
    Option "Emulate3Buttons" "no"
    Option "ZAxisMapping" "4 5"
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
    BusID          "PCI:3:0:0"
#####new
    Option         "NvAGP" "0"
    Option         "CoolBits" "2"
    Option         "BackingStore" "True"
    Option         "RenderAccel" "True"
    Option         "NoFlip" "False"
    Option         "NoRenderExtension" "False"
    Option         "MultisampleCompatibility" "True"
    Option         "OnDemandVBlankInterrupts" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RandRRotation" "True"
    Option         "UseCompositeWrapper" "True"
    Option         "SLi" "AA"
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

 
```

---

### Post by bodhi.zazen on 2009-12-27
I do not see anything wrong with your xorg. Perhaps change which device is default ?

---

### Post by Groundswell on 2009-12-27
no beans, i'm starting to suspect that it's not recognized as a pointing device since it's part of the joystick. the axis's of the mini-mouse show up in jscalibrator. so if there were a way to tell xserver to listen to the device for the specific 2 axis's for mouse input it may work. i won't die if i never get it working, but it be cool if it would, still not worth going back to windows for a mini-mouse

---

### Post by Groundswell on 2010-01-01
bumps, anyone out there have any ideas?

---


---
title: "30&quot; monitor resolution problems"
date: 2009-11-19
forum: General Help
---

### Post by Mooseknuckle on 2009-11-19
Hello.

I'm running Ubuntu 9.10 (Koala)

I have a Dell 3007WFP-HC 30" Monitor.
I have an NVidia GeForce 8400 GS Graphics card.

Using nvidia-settings, the best display I can get is 1280X800!?  It's awful!  It's pixelated and chunky.   I know the GeForce 8 series can do better than this!

I've tried using the opensource drivers via System -> Administration -> Hardware Drivers.

I've downloaded the latest NVidia 64-bit (yes my machine is 64-bit) drivers: NVIDIA-Linux-x86_64-190.42-pkg2.run

Nothing I do seems to change a darn thing.

I even tried creating a file: /etc/default/linux-restricted-modules-common and adding the contents:
DISABLED_MODULES="nv nvidia_new"

to no avail.

Below is the current contents of my /etc/X11/xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    49.31 - 98.71
        VertRefresh  60.0
        VendorName   "Dell"
        ModelName    "3007WFP-HC"
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
        Viewport    0 0
        Depth       24
        Modes      "2560x1600" "1600x1200" "1600x1024" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480" "640x400"
    EndSubSection
EndSection


The modes that show up in my resolution selector are nothing like the ones specified above.

If anyone knows of anything I might be able to do to solve this, I'm all ears... Thanks!

---


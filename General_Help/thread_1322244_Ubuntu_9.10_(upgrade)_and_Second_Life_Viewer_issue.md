---
title: "Ubuntu 9.10 (upgrade) and Second Life Viewer issues"
date: 2009-11-10
forum: General Help
---

### Post by mbogucki on 2009-11-10
Hello All,

I've got a mystery/issue here. I recently upgraded to Ubuntu 9.10 and after fixing the various graphics issues (including a full re-install of nvidia drivers 185.18.36), I noticed a particular problem that's occurring when I'm running either Emerald(950) or the standard second life viewer (version 1.23.5.136274).

If I have several apps running such as gimp and chrome; when I select gimp then try to select back to Emerald, emerald freezes. If I then select gimp, or another app, I see that emerald starts up again (various animations, particles, chat,etc).... If I reselect emerald it freezes again.

To get emerald running again, I need to either minimize/un-minimize the window or select the window with the mouse and move it slightly.

I've only noticed this occuring when Secondlife/Emerald is running and it only affects Second Life/ Emerald. Switching between gimp, chrome, firefox, etc doesn't present these issues.

Note: I'm also running a three-headed display using a pair of Nvidia GTX 260 graphics cards. This is running with xinerama and twinview enabled.

As a quick test, I've downgraded my xorg.conf file to run on a single display and the issue goes away, so I suspect that it has something to do with my xorg configuration or xinerama/twinview.

Here is a copy of my xorg.conf file:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0" 0 0
    Screen       "Screen1" LeftOf "Screen0"
    #InputDevice    "Keyboard0" "CoreKeyboard"
    #InputDevice    "Mouse0" "CorePointer"
    Option       "Xinerama" "True"
EndSection

Section "Module"
    Load           "ddc"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
    Load           "record"
    Load           "bitmap"
    Load           "freetype"
    Load           "speedo"
    Load           "type1"
    Load           "vbe"
    Load           "int10"
   #Load   "fbdevhw"       ## Added 070607
EndSection



Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "True"
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
    ModelName      "DELL E228WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    BusID          "PCI:3:0:0"
EndSection



Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "ConnectedMonitor" "LCD,LCD"
#    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "ConnectedMonitor" "LCD"
#    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
   Option    "Composite" "Disable"
EndSection

Has anyone else seen this particular issue? I'm stumped....

And sorry for the long winded question. Thank you. ^_^

--Mike

---


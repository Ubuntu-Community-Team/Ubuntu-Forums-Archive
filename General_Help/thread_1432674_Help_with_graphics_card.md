---
title: "Help with graphics card"
date: 2010-03-18
forum: General Help
---

### Post by joshcrack on 2010-03-18
I was wondering if anyone could help me with a graphics card problem that I have.
I have a Diamond Multimedia Stealth II g460 card with the intel i740 chip. on an old computer.

After trying for 5 days... I finally got the resolution problem fixed. And the funny thing is that it did it automatically when I generated a xorg.conf file using the steps described here:

[HTML]http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html[/HTML]But I still got more problems... When I have a window open and I move the window around, it looks like the frame rate is so low. I dont fully know how to explain it but...
like when I scroll down a page on the browser, the page looks like it is struggling to move and it crawls down instead of flowing smoothly. Please help someone...

This is my xorg.conf
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dbe"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      430   270    # mm
    Identifier   "Monitor0"
    VendorName   "SAM"
    ModelName    "SyncMaster"
    HorizSync    30.0 - 81.0
    VertRefresh  56.0 - 75.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "SDRAM"                  # [<bool>]
        #Option     "SGRAM"                  # [<bool>]
        #Option     "SlowRam"                # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "UsePIO"                 # [<bool>]
        #Option     "VGACompat"              # [<bool>]
    Identifier  "Card0"
    Driver      "i740"
    VendorName  "Intel Corporation"
    BoardName   "82740 (i740) AGP Graphics Accelerator"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by joshcrack on 2010-03-18
help someone?

---


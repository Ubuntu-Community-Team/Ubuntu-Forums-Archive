---
title: "Nouveau driver"
date: 2010-09-22
forum: General Help
---

### Post by Wiwa94 on 2010-09-22
I have been told that I need this nouveaux driver. Would be much appreciated if you could help out.

My computer is pretty old, 3.06 GHz processor, 1Gb RAM, Intel 82845G/GL/GE/PE/GV Graphics controller (yes I know that's awful so don't tell me, I am on my way to buying a new graphics card)

---

### Post by DarthScape on 2010-09-22
> **Wiwa94 said:**
> I have been told that I need this nouveaux driver. Would be much appreciated if you could help out.

My computer is pretty old, 3.06 GHz processor, 1Gb RAM, Intel 82845G/GL/GE/PE/GV Graphics controller (yes I know that's awful so don't tell me, I am on my way to buying a new graphics card)

nouveau is only for nvidia graphics, intel should have an open source driver that comes with most distros

---

### Post by Wiwa94 on 2010-09-22
Also: Intel driver, want rid.

Xorg.conf:

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
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
    Load  "extmod"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
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

---

### Post by coffeecat on 2010-09-22
> **Wiwa94 said:**
> Also: Intel driver, want rid.

Why do you want to be rid of the intel driver? No intel driver = no GUI.

Also, where did you get that xorg.conf? The last time I saw an xorg.conf as long as that, a flock of pterodactyls flew past. :-s

:wink:

Which version of Ubuntu are you using?

---


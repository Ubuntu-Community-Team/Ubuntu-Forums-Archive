---
title: "Rebooted, Xorg says No Valid Modes"
date: 2010-01-31
forum: General Help
---

### Post by Sensiva on 2010-01-31
I have a Dell Optiplex 755 workstation with Intel Q35 VGA chipset, and using Karmic amd64, everything was working fine, but I rebooted my pc yesterday after 6 days of uptime , then xorg gave an error of No Valid Modes and suggesting to run in low graphix mood, any suggestions?

---

### Post by lidex on 2010-01-31
> **Sensiva said:**
> I have a Dell Optiplex 755 workstation with Intel Q35 VGA chipset, and using Karmic amd64, everything was working fine, but I rebooted my pc yesterday after 6 days of uptime , then xorg gave an error of No Valid Modes and suggesting to run in low graphix mood, any suggestions?

Have you edited your xorg.conf file?
Can you post it here?
Sounds like you made changes somewhere that weren't reflected until you rebooted.

---

### Post by lidex on 2010-01-31
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
[http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html")
[http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html]("http://www.webupd8.org/2009/05/reverting-xorg-video-intel-driver-of.html")

---

### Post by Sensiva on 2010-02-01
No I didn't edit xorg.conf or any files. This is weird, everything was just fine for six days, I only rebooted to do some stuff in Windows and rebooted back to Ubuntu to find that error msg.

I left the PC off for about six hours and turned it back on to find that everything is back to normal. This never happened with Fedora, Debian or even Windows.

xorg.conf
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
    Load  "dri2"
    Load  "glx"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load  "dri"
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
    Horizsync    30.0-140.0
    Vertrefresh    50.0-160.0
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
        #Option     "NoDDC"                  "True"
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82Q35 Express Integrated Graphics Controller"
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
        Virtual    1600    1200
    EndSubSection
EndSection

```

---


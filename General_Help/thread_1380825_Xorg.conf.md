---
title: "Xorg.conf"
date: 2010-01-14
forum: General Help
---

### Post by wirate on 2010-01-14
My hardware is capable of 1200x900 resolution. I used to get this resolution by putting xrandr lines in "/etc/gdm/Xsession". Then i decided to do it with Xorg.conf. I created /etc/X11/Xorg.conf and put this in there
> 
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
    Load  "record"
    Load  "dri2"
    Load  "extmod"
    Load  "glx"
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
    Modeline "1200x900_75.00"  114.00  1200 1280 1408 1616  900 903 907 942 -hsync +vsync
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
    BoardName   "82G33/G31 Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
    Option "Monitor0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1200x900_75.00"
    EndSubSection
EndSection


But i dont get the desired resolution. What am I doing wrong? How can I make sure if this file is even being used?

---

### Post by john newbuntu on 2010-01-14
For a moment, got distracted by your icon there.  Anyway read up about xrandr on Karmic:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by khelben1979 on 2010-01-14
Have you tried with [dexconf]("https://www.cs.drexel.edu/cgi-bin/manServer.pl/usr/share/man/man1/dexconf.1")?

---

### Post by stoneage on 2010-01-14
A couple of differences I have in my xorg.conf are these:-
> Section "Monitor"
    ModelName      "CRT-0"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Modeline "1440x900_75.00" 136.49 1440 1536 1688 1936 900 901 904 940 -HSync +Vsync 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Option 	    "metamodes" "1440x900_75 +0+0"  
    EndSubSection

I can't say it will fix it, but if you are looking for something to try......

Obviously you would use the Horizsync and VertRefresh rates for your particular monitor.

---

### Post by wirate on 2010-01-16
How can I make sure if this file is even being used?

---

### Post by icanreachit on 2010-01-17
I'm rather curious as well, need to modify the resolutions available and have successfully created the xorg.conf but the option is not appearing in my display menu.

Thanks!

---

### Post by falconindy on 2010-01-17
> **wirate said:**
> How can I make sure if this file is even being used?

As per 'man xorg.conf', X looks in a variety of places for this file...

```
           /etc/X11/<cmdline>
           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf-4
           **/etc/X11/xorg.conf**
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf-4
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf-4
           /usr/lib/X11/xorg.conf
```
The first 2 are applicable if you manually start X and use the -config option to specify an xorg.conf file. The next two use an environment variable. The bolded entry is the historical location of xorg.conf in Ubuntu.

---


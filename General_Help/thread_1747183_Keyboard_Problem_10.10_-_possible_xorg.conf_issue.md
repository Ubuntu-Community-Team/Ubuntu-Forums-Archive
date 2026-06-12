---
title: "Keyboard Problem 10.10 - possible xorg.conf issue?"
date: 2011-05-02
forum: General Help
---

### Post by 1984dc on 2011-05-02
[B]Hello every1  ):P

I have been having some trouble with my keyboard cuting out. The keyboard was fine after installation but now it cuts out constantly. I can revive the keyboard for enough time for me to be able to log in and then it will cut out immediately afterwards. The keyboard will run on a live cd and would probably run in the shell.

I think it may be a problem with my xorg.conf (here is a printout of the xorg.0.log):[/B]

[COLOR=Blue]www.ubuntu.com/support) 
[    14.781] Current version of pixman: 0.18.4
[    14.781]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[    14.781] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.782] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 27 20:50:47 2011
[    14.782] (==) Using config file: "/etc/X11/xorg.conf"
[    14.782] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[COLOR=Red][    14.783] Data incomplete in file /etc/X11/xorg.conf
    Undefined InputDevice "Keyboard0" referenced by ServerLayout "X.org Configured".[/COLOR]
[    14.783] (EE) Problem parsing the config file
[    14.783] (EE) Error parsing the config file
[    14.783] 
Fatal server error:
[    14.783] no screens found
[    14.783] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
[    14.783] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    14.783] 
[    14.783]  ddxSigGiveUp: Closing log

[COLOR=Black]**My xorg.conf file looks like:**

[/COLOR][/COLOR][COLOR=Navy]Section "ServerLayout"
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
    Load  "glx"
    Load  "dbe"
    Load  "dri2"
    Load  "extmod"
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
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "MacModel"               # <str>
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Option      "Reverse DDC"        "on"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:240:16:0"
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
[/COLOR][COLOR=Blue][COLOR=Black]
[B]_Here_ is the output of:

[/B][/COLOR][/COLOR]```
lsusb -v
```[COLOR=Black]**_[SIZE=3][Here]("http://pastebin.com/v0ECsDdv")[/SIZE]_**[/COLOR]

**Any help on this would be hugely appreciated. I don't really know what happened as the keyboard seemed to work fine with the original keyboard setup after installation (and works perfectly in mac os x). I deleted and regenerated the xorg.conf file and i tried another mac keyboard which had exactly the same problem. I also tried googling for a guide to troubleshoot Powerpc Linux keyboard problems, but i couldn't find anything specific there either  **[B]:confused:

All the best.

Dc
[/B]

---

### Post by 1984dc on 2011-05-03
Bump.

---

### Post by 1984dc on 2011-05-04
Bump.

---

### Post by 1984dc on 2011-05-11
Bump.

---

### Post by 1984dc on 2011-05-15
I might upgrade to the 11.04 natty daily build. Any ideas anyone?

---

### Post by enimeizoo on 2011-05-15
When you boot from livecd, is the xorg.conf the same? If not, you could try to replace the keyboard entry in your xorg.cong by the one on the livecd.

---

### Post by 1984dc on 2011-05-22
Yes it did work from the Live CD, but thats pretty irrelivant now as i have upgraded to Natty and everything seems to be working fine there (so far!).
 
Many thanks for all your help with this.
 
All the best.
 
Dc

---


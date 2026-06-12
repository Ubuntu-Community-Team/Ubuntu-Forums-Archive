---
title: "Xorg dual monitor"
date: 2011-07-18
forum: General Help
---

### Post by sandyd on 2011-07-18
Im currently having a nasty problem with Xorg and my laptop.

I have a single graphics card in my laptop.

At home, its connected to a HDMI monitor, elsewhere, its not.

The problem is that Xorg -configure doesn't generate the correct dual monitor setup. The resolution has to be manually set (see the modes section), in order for it to be right.

Is there a way to get the laptop screen working at one resolution, while the HDMI screen works at another?

Xorg.conf
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib64/xorg/modules"
        FontPath     "/usr/share/fonts/corefonts/"
        FontPath     "/usr/share/fonts/cantarell/"
        FontPath     "/usr/share/fonts/default/"
        FontPath     "/usr/share/fonts/dejavu/"
        FontPath     "/usr/share/fonts/unifont/"
        FontPath     "/usr/share/fonts/util/"
        FontPath     "/usr/share/fonts/windows"
EndSection

Section "Module"
        Load  "dbe"
        Load  "dri"
        Load  "dri2"
        Load  "extmod"
        Load  "glx"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      370   230     # mm
        Identifier   "Monitor0"
        VendorName   "LPL"
        ModelName    "0"
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
        Option     "BusType" "PCIE"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        Option     "GARTSize" "64"              # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        Option     "EnableDepthMoves" "on"       # [<bool>]
        Option     "EnablePageFlip" "1"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        Option     "AccelDFS" "1"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        Option     "ColorTiling" "1"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        Option     "RenderAccel" "true"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        Option     "AccelMethod" "EXA"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
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
        Identifier  "Card0"
        Driver      "radeon"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
                Modes "1920x1080"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                Modes "1920x1080"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                Modes "1920x1080"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                Modes "1920x1080"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes "1920x1080"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1920x1080"
        EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

```

Xrandr
```
LVDS connected (normal left inverted right x axis y axis)
   1440x900       60.8 +
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  

```

I don't need any other fancy stuff. I just need the monitors to show the correct resolution when their connected or not connected.

---


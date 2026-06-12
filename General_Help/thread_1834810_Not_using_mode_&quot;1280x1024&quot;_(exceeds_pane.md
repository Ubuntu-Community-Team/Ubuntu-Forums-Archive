---
title: "Not using mode &quot;1280x1024&quot; (exceeds panel dimensions) Chipset: &quot;852GM/855GM&quot;"
date: 2011-08-28
forum: General Help
---

### Post by Merome on 2011-08-28
I'm new to ubuntu, I installed it on an old laptop Maxdata ECO 4200X, with intel graphic card i852/855GM

I can see 3 resolutions in the display preferences, maximum : 1024x768.

Before, this laptop was running xp with resolution 1280x1024.

I would like to use 1280x1024 with ubuntu but I can't.

If it can helps :

```

> xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       61.3 +   60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```
```

> xrandr --newmode "1280x1024" 109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
> xrandr --addmode LVDS1 "1280x1024"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26


```My xorg.conf :

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    Screen      3  "Screen3" RightOf "Screen2"
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
    Load  "dbe"
    Load  "glx"
    Load  "dri"
    Load  "extmod"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
   [B] Modeline "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
        Option        "PreferredMode" "1280x1024"[/B]
        Option        "TargetRefresh" "60"
    Option "UseEdidFreqs" "false"
    Option "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    Modeline "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Modeline "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor3"
    Modeline "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "LinearFramebuffer"      # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "TripleBuffer"           # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:1"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card2"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card3"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes         "1280x1024" "800x600" "640x480"
        Virtual 1280 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
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

Section "Screen"
    Identifier "Screen3"
    Device     "Card3"
    Monitor    "Monitor3"
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
Some interesting parts of my Xorg.0.log

```

[    27.734] (II) intel(0): Output LVDS1 using monitor section Monitor0
[    27.734] (**) intel(0): Option "PreferredMode" "1280x1024"

[    28.036] (II) intel(0): EDID for output LVDS1
[    28.036] (II) intel(0): Manufacturer: CPT  Model: bb9  Serial#: 0
[    28.036] (II) intel(0): Year: 2004  Week: 39
[    28.036] (II) intel(0): EDID Version: 1.2
[    28.036] (II) intel(0): Digital Display Input
[    28.036] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 23

[    28.036] (II) intel(0): Supported detailed timing:
[    28.036] (II) intel(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    28.036] (II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1320 h_border: 0
[    28.036] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0

[    28.037] (II) intel(0): Printing DDC gathered Modelines:
[    28.037] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
**[    28.037] (II) intel(0): Not using mode "1280x1024" (exceeds panel dimensions)**
[    28.037] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.037] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    28.038] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    28.038] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.038] (II) intel(0): Printing probed modes for output LVDS1
[    28.038] (II) intel(0): Modeline "1024x768"x61.3   65.00  1024 1048 1184 1320  768 771 777 803 -hsync -vsync (49.2 kHz)
[    28.038] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.038] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.038] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    28.038] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.325] (II) intel(0): EDID for output VGA1
[    28.325] (II) intel(0): Output LVDS1 connected
[    28.325] (II) intel(0): Output VGA1 disconnected
[    28.325] (II) intel(0): Using exact sizes for initial modes
[    28.325] (II) intel(0): Output LVDS1 using initial mode 1024x768

[    28.327] (II) intel(0): Allocated new frame buffer 1280x1024 stride 8192, tiled

```


Any help would be appreciated...

---

### Post by Ed_Ziffel on 2011-08-28
You are no doubt exceeding the max pixel count of your display panel.  Think trying to force an old style tv to play HD movies.  Your panel may be 1280 x 720 for instance.  Look up your laptop on line and check the specs.  Then set the display in preferences accordingly.

---

### Post by Merome on 2011-08-28
> **Ed_Ziffel said:**
> You are no doubt exceeding the max pixel count of your display panel.  Think trying to force an old style tv to play HD movies.  Your panel may be 1280 x 720 for instance.  Look up your laptop on line and check the specs.  Then set the display in preferences accordingly.

XP was running fine in 1280x1024. Ubuntu is not able to do the same ?

---


---
title: "Desktop effects could not be enabled"
date: 2009-12-11
forum: General Help
---

### Post by rahilm on 2009-12-11
hi.. i have installed ubuntu on my friend's computer. When I try to enable desktop effects it gives an error that Desktop effects could not be enabled.

lscpi | grep VGA gives
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

Please help!!

---

### Post by tom66 on 2009-12-11
It might be that the chipset you have there is not capable of 3D effects. It depends on its age or model. 

I just looked up that chip, it is nearly 7 years old. It is unlikely that any 3D effect or game will support that. Your friend's computer will need a new graphics card. Any cheap £20 one will do the job fine.

---

### Post by delectate on 2009-12-11
maybe it's too old to enable 3d effects

Try to find a driver ,then install it.

---

### Post by rahilm on 2009-12-11
i found this out..but i can't understand how to do it in karmic

[HTML]http://ubuntuforums.org/showthread.php?t=675870[/HTML]

---

### Post by ronnielsen1 on 2009-12-12
It's not too old. I have the same issue with the same card. It's picked up automatically by parsix live cd but unfortunately I'm not knowledgeable enough to figure out what driver it's using. The parsix xorg.conf is listed below if that helps. Maybe it would help someone to figure out the driver it's using?

> Section "ServerLayout"
    Identifier    "XFree86 Configured"
    Screen        0    "Screen0"    0    0
    InputDevice    "Keyboard0"        "CoreKeyboard"
# PS/2 Mouse not detected
# Serial Mouse not detected
    InputDevice    "USB Mouse"        "CorePointer"
# ALPS TouchPad not detected
# Synaptics TouchPad not detected
EndSection

Section "ServerFlags"
    Option        "AllowMouseOpenFail"    "true"
    
EndSection

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load        "ddc"        # ddc probing of monitor
    #Load        "GLcore"
    Load        "bitmap"    # bitmap-fonts
    Load        "type1"
# TouchPad not detected
EndSection

Section "InputDevice"
    Identifier    "Keyboard0"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"        "xorg"
    Option         "XkbOptions"    "grp:alt_shift_toggle"
    Option         "XkbLayout" "us,ir"
    Option        "XkbModel"        "pc105"

EndSection

Section "InputDevice"
    Identifier    "Serial Mouse"
    Driver        "mouse"
    Option        "Protocol"            "Microsoft"
    Option        "Device"            "/dev/ttyS0"
    Option        "Emulate3Buttons"    "true"
    Option        "Emulate3Timeout"    "70"
    Option        "SendCoreEvents"    "true"
EndSection

Section "InputDevice"
    Identifier    "PS/2 Mouse"
    Driver        "mouse"
    Option        "Protocol"          "IMPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Device"            "/dev/psaux"
    Option        "Emulate3Buttons"    "true"
    Option        "Emulate3Timeout"    "70"
    Option        "SendCoreEvents"    "true"
EndSection

Section "InputDevice"
    Identifier    "USB Mouse"
    Driver        "mouse"
    Option        "Device"            "/dev/input/mice"
    Option        "SendCoreEvents"    "true"
    Option        "Protocol"            "IMPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Buttons"            "5"
EndSection

Section "InputDevice"
    Identifier    "ALPS TouchPad"
    Driver        "synaptics"
    Option        "Device"              "/dev/psaux"
    Option        "Protocol"                "auto-dev"
    Option        "LeftEdge"                "120"
    Option        "RightEdge"                "830"
    Option        "TopEdge"                  "120"
    Option        "BottomEdge"            "650"
    Option        "FingerLow"                 "14"
    Option        "FingerHigh"             "15"
    Option        "MaxTapTime"            "180"
    Option        "MaxTapMove"            "110"
    Option        "EmulateMidButtonTime"    "75"
    Option        "VertScrollDelta"       "20"
    Option        "HorizScrollDelta"      "20"
    Option        "MinSpeed"                "0.7"
    Option        "MaxSpeed"                "3"
    Option        "AccelFactor"            "0.025"
    Option        "EdgeMotionMinSpeed"    "15"
    Option        "EdgeMotionMaxSpeed"    "15"
    Option        "UpDownScrolling"        "1"
    Option        "CircularScrolling"        "1"
    Option        "CircScrollDelta"        "0.1"
    Option        "CircScrollTrigger"        "2"
EndSection

Section "InputDevice"
    Identifier    "Synaptics TouchPad"
    Driver        "synaptics"
    Option        "Device"            "/dev/psaux"
    Option        "Protocol"            "auto-dev"
    Option        "LeftEdge"            "1700"
    Option        "RightEdge"            "5300"
    Option        "TopEdge"            "1700"
    Option        "BottomEdge"        "4200"
    Option        "FingerLow"            "25"
    Option        "FingerHigh"        "30"
    Option        "MaxTapTime"        "180"
    Option        "MaxTapMove"        "220"
    Option        "VertScrollDelta"    "100"
    Option        "MinSpeed"            "0.06"
    Option        "MaxSpeed"            "0.12"
    Option        "AccelFactor"        "0.0010"
    Option        "SHMConfig"            "on"
    Option        "Repeater"            "/dev/ps2mouse"
EndSection

# Auto-generated by PARSIX mkxf86config

Section "Monitor"
    Identifier    "Monitor0"
    Option    "DPMS"    "true"
    VendorName    "NEC"
    ModelName    "NEC660e"
    HorizSync 30 - 81 # DDC-probed
    VertRefresh 55 - 76 # DDC-probed
    # These are the DDC-probed settings reported by your monitor.
    # 1280x1024, 75.0Hz; hfreq=79.98, vfreq=75.03
    ModeLine "1280x1024"    135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    # 1152x864, 75.0Hz; hfreq=67.50, vfreq=75.00
    ModeLine "1152x864"    108.00 1152 1216 1344 1600  864  865  868  900 +hsync +vsync
    # 1024x768, 75.0Hz; hfreq=60.02, vfreq=75.03
    ModeLine "1024x768"     78.75 1024 1040 1136 1312  768  769  772  800 +hsync +vsync
    # 1024x768, 70.0Hz; hfreq=56.48, vfreq=70.07
    ModeLine "1024x768"     75.00 1024 1048 1184 1328  768  771  777  806 -hsync -vsync
    # 800x600, 75.0Hz; hfreq=46.88, vfreq=75.00
    ModeLine "800x600"     49.50  800  816  896 1056  600  601  604  625 +hsync +vsync
    # 800x600, 72.0Hz; hfreq=48.08, vfreq=72.19
    ModeLine "800x600"     50.00  800  856  976 1040  600  637  643  666 +hsync +vsync
    # 800x600, 60.0Hz; hfreq=37.88, vfreq=60.32
    ModeLine "800x600"     40.00  800  840  968 1056  600  601  605  628 +hsync +vsync
    # 640x480, 75.0Hz; hfreq=37.50, vfreq=75.00
    ModeLine "640x480"     31.50  640  656  720  840  480  481  484  500 -hsync -vsync
    # 640x480, 72.0Hz; hfreq=37.86, vfreq=72.81
    ModeLine "640x480"     31.50  640  656  696  816  480  481  484  504 -hsync -vsync
    # 640x480, 60.0Hz; hfreq=31.47, vfreq=59.94
    ModeLine "640x480"     25.17  640  648  744  784  480  482  484  509 -hsync -vsync
    # Extended modelines with GTF timings
    # 640x480 @ 100.00 Hz (GTF) hsync: 50.90 kHz; pclk: 43.16 MHz
    ModeLine "640x480"  43.16  640 680 744 848  480 481 484 509  -HSync +Vsync
    # 768x576 @ 60.00 Hz (GTF) hsync: 35.82 kHz; pclk: 34.96 MHz
    ModeLine "768x576"  34.96  768 792 872 976  576 577 580 597  -HSync +Vsync
    # 768x576 @ 72.00 Hz (GTF) hsync: 43.27 kHz; pclk: 42.93 MHz
    ModeLine "768x576"  42.93  768 800 880 992  576 577 580 601  -HSync +Vsync
    # 768x576 @ 75.00 Hz (GTF) hsync: 45.15 kHz; pclk: 45.51 MHz
    ModeLine "768x576"  45.51  768 808 888 1008  576 577 580 602  -HSync +Vsync
    # 768x576 @ 85.00 Hz (GTF) hsync: 51.42 kHz; pclk: 51.84 MHz
    ModeLine "768x576"  51.84  768 808 888 1008  576 577 580 605  -HSync +Vsync
    # 768x576 @ 100.00 Hz (GTF) hsync: 61.10 kHz; pclk: 62.57 MHz
    ModeLine "768x576"  62.57  768 816 896 1024  576 577 580 611  -HSync +Vsync
    # 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
    ModeLine "800x600"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
    # 1024x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 48.96 MHz
    ModeLine "1024x600"  48.96  1024 1064 1168 1312  600 601 604 622  -HSync +Vsync
    # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
    ModeLine "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
    # 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
    ModeLine "1152x864"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
    # 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
    ModeLine "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907  -HSync +Vsync
    # 1152x864 @ 100.00 Hz (GTF) hsync: 91.50 kHz; pclk: 143.47 MHz
    ModeLine "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915  -HSync +Vsync
    # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
    ModeLine "1280x768"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
    # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
    ModeLine "1280x800"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
    # 1280x960 @ 72.00 Hz (GTF) hsync: 72.07 kHz; pclk: 124.54 MHz
    ModeLine "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync
    # 1280x960 @ 75.00 Hz (GTF) hsync: 75.15 kHz; pclk: 129.86 MHz
    ModeLine "1280x960"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync
    # 1280x960 @ 100.00 Hz (GTF) hsync: 101.70 kHz; pclk: 178.99 MHz
    ModeLine "1280x960"  178.99  1280 1376 1520 1760  960 961 964 1017  -HSync +Vsync
    # 1280x1024 @ 100.00 Hz (GTF) hsync: 108.50 kHz; pclk: 190.96 MHz
    ModeLine "1280x1024"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
    # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
    ModeLine "1368x768"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
    # 1400x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 122.61 MHz
    ModeLine "1400x1050"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync
    # 1400x1050 @ 72.00 Hz (GTF) hsync: 78.77 kHz; pclk: 149.34 MHz
    ModeLine "1400x1050"  149.34  1400 1496 1648 1896  1050 1051 1054 1094  -HSync +Vsync
    # 1400x1050 @ 75.00 Hz (GTF) hsync: 82.20 kHz; pclk: 155.85 MHz
    ModeLine "1400x1050"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
    # 1400x1050 @ 85.00 Hz (GTF) hsync: 93.76 kHz; pclk: 179.26 MHz
    ModeLine "1400x1050"  179.26  1400 1504 1656 1912  1050 1051 1054 1103  -HSync +Vsync
    # 1400x1050 @ 100.00 Hz (GTF) hsync: 111.20 kHz; pclk: 214.39 MHz
    ModeLine "1400x1050"  214.39  1400 1512 1664 1928  1050 1051 1054 1112  -HSync +Vsync
    # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
    ModeLine "1440x900"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
    # 1440x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 126.27 MHz
    ModeLine "1440x1050"  126.27  1440 1536 1688 1936  1050 1051 1054 1087  -HSync +Vsync
    # 1600x1200 @ 100.00 Hz (GTF) hsync: 127.10 kHz; pclk: 280.64 MHz
    ModeLine "1600x1200"  280.64  1600 1728 1904 2208  1200 1201 1204 1271  -HSync +Vsync
    # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
    ModeLine "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
    # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
    ModeLine "1920x1200"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Section "Device"
    Option        "RenderAccel"            "1"
    Option       "XAANoOffscreenPixmaps"    "true"
    Option        "AddARGBGLXVisuals"     "true"
    Option        "AccelMethod"        "XAA" 

    ### Available Driver options are:-
    # sw_cursor is needed for some ati and radeon cards
    #Option        "sw_cursor"
    #Option        "hw_cursor"
    #Option        "NoAccel"
    #Option        "ShowCache"
    #Option        "ShadowFB"
    #Option        "UseFBDev"
    #Option        "Rotate"
    Identifier    "Card0"
    # The following line is auto-generated by PARSIX mkxf86config
    Driver        "intel"
    VendorName    "All"
    BoardName    "All"
    #BusID        "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Card0"
    Monitor        "Monitor0"
    DefaultColorDepth 24
    SubSection "Display"
        Depth    8
        Modes "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option   "Composite"   "Enable"
EndSection

---

### Post by Kevbert on 2009-12-12
Please take a look at [[COLOR="Red"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/296833/") especially post #8.

---

### Post by rahilm on 2009-12-12
i'll try it. thanx for the help

---

### Post by ronnielsen1 on 2009-12-16
Thank you Kevbert. Works great!

---


---
title: "Configuring Ati Tv-out"
date: 2006-04-17
forum: General Help
---

### Post by damotor on 2006-04-17
Hi.
I have a laptop with breezy and the official ati drivers installed working. The only problem is that my screen is 16:9 and my TVs are 4:3 and when I connect them by the S-video output I can only see a part of the desktop.
How could I configure it in order to have a 16:9 resolution in my laptop and 4.3 in the S-video?.

Thanks.

Here is my xorg.conf file
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig Screen 0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "GLcore"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "es"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "Monitor"
        Identifier   "Monitor gen\uffffrico"
        ModeLine     "1280x800@60" 83.9 1280 1312 1624 1656 800 816 824 841
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor    "Monitor gen\uffffrico"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig Screen 0"
        Device     "ATI Graphics Adapter 0"
        Monitor    "aticonfig Monitor 0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

---


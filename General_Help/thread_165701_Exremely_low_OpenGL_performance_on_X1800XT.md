---
title: "Exremely low OpenGL performance on X1800XT"
date: 2006-04-25
forum: General Help
---

### Post by John64 on 2006-04-25
I have the drivers set up properly, but i get pathetic OpenGL Performance.  Unlike my old 7800GTX which could do glxgears so fast it looked like cylinders not gears, my X1800XT looks like its about as fast as a 33RPM Phono.

All the GL Screensavers are very slow.  This is with the ubuntu kernel and a kernel.org/ck3 kernel

Any ideas?

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

Abridged xorg.conf
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig Screen 0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
...
EndSection

Section "Module"
        Load  "i2c"
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
        ...
EndSection

Section "Monitor"
        Identifier   "DELL 2005FPW"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        Option      "(null)"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:3:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "DELL 2005FPW"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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

### Post by domel138 on 2006-04-26
How do you get the HW acceleration on X1800XT do you have 256MB or 512MB. I've try 5 distribution's and i in all I must use "NoDIR" Option to get X work. I've got 512MB version.

---

### Post by John64 on 2006-04-29
i use the instructions at the ATI Linux Driver Wiki (dont have the address this second, i am in windows).  They are awesome.  Ubuntu is the best distro out there if you want something that works out of the box but is very upgradable.

This card is garbage for linux.  I am allmost ready to swap it out for a 7900GT

---


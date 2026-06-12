---
title: "ATI drivers + JACK + LSM kernel module"
date: 2005-02-11
forum: General Help
---

### Post by bobmitch on 2005-02-11
Hi all,

Ok, I had JACK + LSM realtime security kernel module running together in realtime mode no problem.  (woot!)

BUT

Once I installed and configured my fglrx ati drivers, jack/realtime stuff just hangs when starting jack in realtime mode.  I can still launch some programs, but opening a terminal and typing , for example, "ps -ef | grep foo" will just do nothing - completely dead... ctl-c does nothing.

I have spoken to the author of jack/ardour, but he is reluctant to help, and rightly so, as it appears to be an issue with fglrx/lsm.

Has anybody else had this problem, or who has any possible fix?

Not, these are not the latest ati drivers, but the ones from warty-universe.

Cheers,
mitch

---

### Post by nantetokuma on 2007-05-31
Hi, I've a similar problem.

I've just install Ubuntu Studio (Feisty Fawn) and my first thing was to try ardour2. Except a problem with screen resolution it worked. I've install ATI drivers with System/Admin/proprietary drivers and screen looks good (except it didn't put the right Vsynchro for the screen). But therefor, could not start Ardour2 anymore... I've try lot of thing until I've uninstall ATI drivers... And ardour works...

I'm going to try install ATI drivers another way.

Hope it helps

Dawidbass

---

### Post by nantetokuma on 2007-06-15
I've reinstall ATI drivers with xorg.conf from my Dapper version, it'ok with it...
I give you my video card and screen sections, if it help somebody...

**xorg.conf**
```
Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        #ajouté voir http://ubuntuforums.org/showthread.php?t=24557
        #Load    "GLcore"
        # Load "extmod" but omit DGA extension - this must be included as is if 
you want to change resolution on the fly
        SubSection "extmod"
            Option "omit xfree86-dga"
        EndSubSection
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection
```
```
Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AU [Radeon 9650]"
        Driver      "fglrx"
        # If X refuses to use the screen resolution you asked for,
        # uncomment this; see "Bugs and Workarounds" for details.
        Option "NoDDC"

        # === Video Overlay for the Xv extension ===
        Option          "VideoOverlay"          "on"

        # === OpenGL Overlay ===
        # Note: When OpenGL Overlay is enabled, Video Overlay
        #       will be disabled automatically
        Option          "OpenGLOverlay"         "off"

        # === Use internal AGP GART support? ===
        # If OpenGL acceleration doesn't work, try using "yes" here
        # and disable the kernel agpgart driver.
        Option          "UseInternalAGPGART"    "no"

        # You don't actually need this next BusID bit - unless maybe you have dual monitors?
        # I've removed it from mine (single monitor only) and all is well.
        # I think it's a leftover from fxglrconfig - doh!
        BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "V995"
        HorizSync    30-96
        VertRefresh  50-150
        Option      "DPMS"
        #ajouter la ligne suivante pour V-freq: 75.00Hz // h-freq: 94.24KHz
        #Modeline  "1600x1200" 242.01 1600 1728 2024 2568   1200 1200 1204 1256
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AU [Radeon 9650]"
        Monitor    "V995"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```
```
Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

dawidbass... on UbuntuStud

---


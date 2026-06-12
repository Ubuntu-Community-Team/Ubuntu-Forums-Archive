---
title: "Dual monitors with Nvidia 7200 GS?"
date: 2011-06-06
forum: General Help
---

### Post by kozimodo on 2011-06-06
Hi all -

I just bought an eVGA graphics card so that I could used a dual monitor setup but I'm having a bear of a time figuring out how to set it up.  Any one gotten it to work with this card?

Cheers!

---

### Post by kozimodo on 2011-06-08
I've gotten the dual head setup working with xrandr:
```
xrandr --output DVI-I-1 --right-of VGA-1
```
I suppose I could put this in a script and start it on login but that seems inelegant to me.

But can't figure out how to set up an xorg.conf file that will do it.  Any help would be much appreciated.  My current xorg.conf file is:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:1:0:0"
	Driver		"nouveau"
        Option          "DVI-I-1" "Left Monitor"
        Option          "VGA-1" "Right Monitor"
EndSection

Section "Monitor"
        Identifier      "Left Monitor"
EndSection

Section "Monitor"
        Identifier      "Right Monitor"
        Option          "Right Of" "Left Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         3200 1080
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

---

### Post by jwcalla on 2011-06-08
Are you open to using the proprietary nvidia driver?  They have a few dual monitor options in their setup program that are pretty easy to configure.

---

### Post by kozimodo on 2011-06-08
I tried the proprietary drivers (the old one, the current one and the x-swat current one) and only 1 monitor is recognized.

---

### Post by jwcalla on 2011-06-08
> **kozimodo said:**
> I tried the proprietary drivers (the old one, the current one and the x-swat current one) and only 1 monitor is recognized.

Good point... that could be because the evil VGA adapter might not have DDC so the video card doesn't know much about the VGA display.  I got around this by adding my monitor manually to the xorg.conf -- with the appropriate HorizSync and VertRefresh numbers (you have to find these for your monitor).

e.g.:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "ViewSonic"
    ModelName      "VP171b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
    # HorizSync source: builtin, VertRefresh source: builtin
    #    HorizSync       28.0 - 55.0
    #    VertRefresh     43.0 - 72.0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "MetaModes" "DFP: 1920x1080 +0+0, CRT: 1280x1024 +1920+0; DFP: 1920x1080 +0+0, CRT: NULL"
        Option         "ConnectedMonitor" "DFP-0, CRT-1"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kozimodo on 2011-06-08
Unfortunately it's the DVI monitor that's not recognized.  I tried setting up the monitor myself in the xorg.conf file but that didn't work either.  Thanks anyway.

I have to think that the Nouveau drivers will work since xrandr gets it right -- it's just a matter of figuring out how to set up the xorg.conf.

---

### Post by kozimodo on 2011-06-08
I got it working following [these]("http://www.granneman.com/techinfo/linux/installation/dualheadhowto.htm") instructions!

For anyone interested, my xorg.conf is:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
	Driver		"nouveau"
        BusID           "PCI:1:0:0"
        Screen		0
EndSection

Section "Device"
        Identifier      "Configured Video Device"
	Driver		"nouveau"
        BusID           "PCI:1:0:0"
        Screen		1
EndSection

Section "Monitor"
        Identifier      "Left Monitor"
        Option	"DPMS"
EndSection

Section "Monitor"
        Identifier      "Right Monitor"
        VendorName	"Gateway"
        ModelName	"FPD1810"
        HorizSync	31 - 61
        VertRefresh	56 - 75
        Option	"DPMS"
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)"
		Monitor	"Left Monitor"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Modes         "1920x1080"
        EndSubSection
EndSection

Section	"Screen"
	Identifier	"Right Screen"
        Device          "nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)"
	Monitor	"Right Monitor"
	DefaultDepth	24
        SubSection "Display"
            Depth           24
            Modes         "1280x1024"
        EndSubSection
EndSection

Section	"ServerFlags"
	Option	"Xinerama"	"ON"
EndSection

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen	0	"Left Screen"	0	0
        Screen	1	"Right Screen"	RightOf	"Left Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

---


---
title: "3 monitors, 2 ati cards, ubuntu 10.10"
date: 2010-11-19
forum: General Help
---

### Post by ryu9 on 2010-11-19
hi there,

i have 2 ati cards. and 3 monitors.

1st ati card - 1 monitor connected via dvi
2nd ati card - 1 monitor connected via dvi, 1 monitor via vga

all 3 monitors should have the same resolution: 1680x1050

i tried to write my own /etc/X11/xorg.conf file, after saving i run:

```
aticonfig --initial
```the program did small changes to my config file. it now looks like this:

```
Section "ServerLayout"
    Identifier     "ryu Layout"
    Screen      0  "scr1-0" 0 0
    Screen         "scr2-0" RightOf "scr1-0"
    Screen         "scr2-1" RightOf "scr2-0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
EndSection

Section "Monitor"
    Identifier   "mon1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Position" "0 0"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "mon2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Position" "0 0"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "mon3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Position" "0 0"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "vesa"
EndSection

Section "Device"
    Identifier  "ati1-0"
    Driver      "fglrx"
    Option        "Capabilities" "0x00000800"
    Option        "TexturedVideoSync" "on"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "ati2-0"
    Driver      "fglrx"
    Option        "Capabilities" "0x00000800"
    Option        "TexturedVideoSync" "on"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "ati2-1"
    Driver      "fglrx"
    Option        "Capabilities" "0x00000800"
    Option        "TexturedVideoSync" "on"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
    SubSection "Display"
        Virtual   5040 1050
    EndSubSection
EndSection

Section "Screen"
    Identifier "scr1-0"
    Device     "ati1-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   1680 1050
        Modes    "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier "scr2-0"
    Device     "ati2-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   1680 1050
        Modes    "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier "scr2-1"
    Device     "ati2-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   1680 1050
        Modes    "1680x1050"
    EndSubSection
EndSection

```It work's. But not as I expected. The thing is. All 3 monitors are working. I can move through all 3 monitors with my mouse - so none of them is mirrored - BUT: the first monitor has a very small resolution - not the one of the other 2, and it's kind of "in the middle". I took a picture. It looks like this:

[IMG]http://bildupload.sro.at/a/images/3mons.jpg[/IMG]

I hope one of you has an idea to fix this problem.
Thanks in advance.

---

### Post by ryu9 on 2010-11-22
I fixed the problem. This is my new xorg.conf.

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[2]-0" 3360 0
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Standardmonitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "1-DFP2"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3360 1680
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-0"
    Device     "amdcccle-Device[2]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by randumnumber on 2010-11-22
huh so changing it to a lower resolution worked? thats odd.

---

### Post by ryu9 on 2010-11-22
No, the one with the lower resolution is just a fallback automatically generated by the ati manager after commiting my changes.

EDIT:

The result, all 3 with 1680x1050:

[IMG]http://bildupload.sro.at/a/images/3mons2.jpg[/IMG]

---

### Post by jpastore on 2011-04-24
I was wondering if I could get your opinion on my xorg.conf

I'm trying to run run triple-head with 2 ATI 5700 series. I have 1 monitor on device 0 and 2 on device 1.

I read through your config and modified mine accordingly. Unfortunately I'm still getting mirroring on the monitors on device 1. Your thoughts would be appreciated.

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option      "aticonfig-Monitor[0]-0"
	BusID       "PCI:8:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	Option      "aticonfig-Monitor[1]-0"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	Option      "aticonfig-Monitor[1]-0"
	BusID       "PCI:7:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



```

---


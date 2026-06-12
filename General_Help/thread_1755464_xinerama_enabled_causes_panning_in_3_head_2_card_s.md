---
title: "xinerama enabled causes panning in 3 head 2 card setup"
date: 2011-05-11
forum: General Help
---

### Post by samjam on 2011-05-11
The new radeon drivers on 11.04 will run at 16bpp which should allow my 3-head setup to work with xinerama and finally allow dragging windows across the whole desktop, but when xinerama is enabled the final monitor pans.

I have a displaylink driver, and an ATI card Chipset: "ATI Radeon HD 3200 Graphics" (ChipID = 0x9612)

I'm using the open source radeon drivers.

The displaylink is screen 0 and the radeon is screen 1.
Initially the 3rd monitor (DVI-0, the right-half of the radeon) correctly displays the second half of the radeon output but it will insist on panning to show the mouse pointer whenever the pointer is within view of the radeon. This means that if the mouse is at the left of monitor 2 (VGA-0, the first radeon output) that that monitor 3 will be a clone of monitor 2.

Only when I move the mouse beyond the end of monitor 2 does monitor 3 begin to pan back to the correct position. But as soon a the mouse is back within the bounds of monitor 2, then monitor three pans back again.

I don't have any "virtual" sections, and everything works fine with xinerama disabled except that I can no longer drag between my displaylink monitors and my radeon monitors.

I attach my xorg.conf

```

Section "ServerLayout"
        Identifier     "m123"
        Screen      0  "screen0" 0 0
        Screen      1  "ATI Screen" RightOf "screen0"
	Option "Xinerama" "off"
	Option "clone" "off"
EndSection

Section "Screen"
	Identifier	"ATI Screen"
	Device	"ATI Device"
	Monitor "ATI Monitor"
        DefaultDepth     16
	DefaultFbBpp	16
EndSection

Section "Device"
	Identifier	"ATI Device"
	Driver "radeon"
        BusID       "PCI:1:5:0"
        Option      "Monitor-VGA-0" "VGA-0"
        Option      "Monitor-DVI-0" "DVI-0"
#	Option      "Monitor-LVDS"  "LVDS"

EndSection

Section "Monitor"
        Identifier   "ATI Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "DVI-0"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "RightOf" "VGA-0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "LVDS"
        Option      "Disable" "true"
#	Option      "Ignore" "true"
EndSection

Section "Monitor"
        Identifier   "VGA-0"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
	Option      "Primary" "true"
EndSection

Section "Screen"
        Identifier "screen0"
        Device "dl0"
        Monitor "monitor0"
        DefaultDepth     16
	Option "NoInt10" "true"
EndSection

Section "Device"
        Identifier      "dl0"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
        Identifier "monitor0"
	Mode "1680x1050"
	    # D: 146.263 MHz, H: 65.296 kHz, V: 59.960 Hz
	    DotClock 146.264
	    HTimings 1680 1784 1960 2240
	    VTimings 1050 1053 1059 1089
	    Flags    "+HSync" "-VSync"
	EndMode
EndSection


```

---

### Post by samjam on 2011-05-11
I found my tip here:
[https://bbs.archlinux.org/viewtopic.php?id=115596](https://bbs.archlinux.org/viewtopic.php?id=115596)

It used the radeon is two cards (which I had tried before) but the answer was to use the radeon "Zaphod Heads" option.

My working xorg.conf is

```

Section "ServerFlags"
	Option "clone" "off"
	Option "Xinerama" "on"
        Option "RandR" "off"
EndSection

Section "ServerLayout"
        Identifier     "m123"
        Screen      0  "DL" 0 0
        Screen      1  "ATI-0" RightOf "DL"
        Screen      2  "ATI-1" RightOf "ATI-0"
EndSection

Section "Screen"
        Identifier "DL"
        Device "dl0"
        Monitor "DL-Monitor"
        DefaultDepth     16
	Option "NoInt10" "true"
EndSection

Section "Screen"
	Identifier	"ATI-0"
	Device	"ATI-Card-0"
	Monitor "VGA-0"
        DefaultDepth     16
	DefaultFbBpp	16
EndSection

Section "Screen"
	Identifier	"ATI-1"
	Device	"ATI-Card-1"
	Monitor "DVI-0"
        DefaultDepth     16
	DefaultFbBpp	16
EndSection

Section "Device"
        Identifier      "dl0"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb1"
EndSection

Section "Device"
	Identifier	"ATI-Card-0"
	Driver "radeon"
        BusID       "PCI:1:5:0"
	Screen 0
	Option "ZaphodHeads" "VGA-0"
EndSection

Section "Device"
	Identifier	"ATI-Card-1"
	Driver "radeon"
        BusID       "PCI:1:5:0"
	Screen 1
	Option "ZaphodHeads" "DVI-0"
EndSection

Section "Monitor"
        Identifier   "DVI-0"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "LVDS"
        Option      "Disable" "true"
#	Option      "Ignore" "true"
EndSection

Section "Monitor"
        Identifier   "VGA-0"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
	Option      "Primary" "true"
EndSection

Section "Monitor"
        Identifier "DL-Monitor"
	Mode "1680x1050"
	    # D: 146.263 MHz, H: 65.296 kHz, V: 59.960 Hz
	    DotClock 146.264
	    HTimings 1680 1784 1960 2240
	    VTimings 1050 1053 1059 1089
	    Flags    "+HSync" "-VSync"
	EndMode
EndSection


```

---


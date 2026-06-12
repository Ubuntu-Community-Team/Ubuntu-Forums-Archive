---
title: "Blank screen (desktop)"
date: 2009-09-21
forum: General Help
---

### Post by coolclassic on 2009-09-21
After a period of inactivity, my desktop LCD screen will go blank no amount of key pressing will reactivate the screen. Using Ctrl, Alt,Del will activate the screen only for a few seconds, only once.  I then have to switch computer off.

Power management has been disabled both in kde and bios.

xorg file:

-------------------------------------------
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"True"
EndSection
---------------------------------------------------------------------

How do you solve this frustrating problem?

I'm using kubuntu 9.04 64bit

---


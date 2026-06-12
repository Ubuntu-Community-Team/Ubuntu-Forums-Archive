---
title: "Nvidia problem"
date: 2009-10-10
forum: General Help
---

### Post by Pizarro on 2009-10-10
I just tried to start extreme tux racer for the first time in months and disaster. The monitor reports out of frequency. I'm sure this happened once when trying knoppix. I assume i need to adjust a setting in the nvidia control panel or something. The graphic card is a gforce7600gs running the recomended restricted driver.All help appreciated.

contents of gedit /etc/X11/xorg.conf   if this helps


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"nvidia"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---


---
title: "Cannot set up monitor"
date: 2009-07-29
forum: General Help
---

### Post by Gunch36 on 2009-07-29
I installed Linux [Baltix]("http://en.wikipedia.org/wiki/Baltix")(based on Ubuntu) on my computer and i have one problem. i can not manage to get the right resolution for my monitor: LG Flatron ez T710BH (dont know where i can get the right HorizSync & VertRefresh for that monitor). The max resolution now is 640x480 but the monitor is 1280x1024.
xorg.conf for my PC:
> ection "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



PLEASE HELP!

---

### Post by CatKiller on 2009-07-29
> **Gunch36 said:**
> LG Flatron ez T710BH (dont know where i can get the right HorizSync & VertRefresh for that monitor).

The [manufacturer's website]("http://www.lge.com/products/model/detail/t710bh.jhtml") has them.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-71
        VertRefresh     50-160
EndSection
```

---

### Post by Gunch36 on 2009-07-29
thanks

---


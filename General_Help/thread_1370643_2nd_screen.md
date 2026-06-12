---
title: "2nd screen"
date: 2010-01-02
forum: General Help
---

### Post by shad0w_crash on 2010-01-02
I got a problem with double screens,. when i display them mirrored everything is just fine, when I disable my 2nd screen (laptop enabled) everyting is fine,. but when I enable the second screen both go black... any clue anyone?

xorx11.conf:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Screen"
    Identifier  "TV Screen"
    Device      "I855GM-1.TV"
    Monitor     "TV"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "800x600"
    EndSubSection
EndSection

```

---

### Post by carolineictwiki on 2010-03-05
Yeah I had the same problem! I messed around in System : Preferences : Display and got it to show the monitor, then was able to use alt+drag to move windows onto my netbook screen, but it's really not the best solution.

---


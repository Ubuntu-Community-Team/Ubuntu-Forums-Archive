---
title: "Help With Mouse Issue"
date: 2010-07-14
forum: General Help
---

### Post by Tak11 on 2010-07-14
whenever I hold a key inside or outside of an application my mouse doesn't respond for several seconds then jumps.
(this is a big problem in First Persion Shooters)

I assume its a problem with xorg.conf 

Xorg.conf

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```


Please help? :)

---

### Post by Tak11 on 2010-07-16
isn't my xorg.conf, i tried disabling the default setting of "disable touch-pad when typing" and saw no difference. I've seen this problem on 3 different computers all the same issue. it is fixed with an external usb mouse the bug only affects touch pads, I'll report it once I'm off work.

---


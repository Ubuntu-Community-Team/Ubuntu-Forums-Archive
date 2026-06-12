---
title: "Dual Screen problem"
date: 2010-11-26
forum: General Help
---

### Post by br4mbi on 2010-11-26
Ok so before the nvidia driver the dual screen worked perfectly (i got 2 screens, and 1 is the main screen and on the other screen i can move programs from screen 1)

But now that I installed the driver, it just won't work anymore...

I've tried following the tutorial here but my xorg is different then the ones in the tutorial...

I'm using a DVI(24") and some VGA monitor I don't know the resolution of.

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

Help would be really appreciated.

---

### Post by papibe on 2010-11-28
Use nvidia-settings to configure your monitors. When you achieve the configuration you want save it to the X conf file:
```
$ sudo nvidia-settings
```

Good Luck!

---


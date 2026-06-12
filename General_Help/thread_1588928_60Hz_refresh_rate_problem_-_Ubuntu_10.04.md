---
title: "60Hz refresh rate problem - Ubuntu 10.04"
date: 2010-10-05
forum: General Help
---

### Post by NekoMaster on 2010-10-05
Hello all. I seem to be having a problem with my display as I cannot seem to get it to run about 60Hz even though it can go as high as 75Hz @ 1600x1200. Its really annoying because I can slightly notice the flickering and its driving me nuts. Also, the fact that everything I've tried hasn't worked is also driving me nuts.

I really need to fix this problem before my eyes bleed from the low refresh. Btw, I have a AOC 9glr 17" monitor connected to a ATI radeon HD 4550 (which can more then handle what I want). One more thing, I already have the drivers for my video card installed, it did nothing to fix this problem...

---

### Post by NekoMaster on 2010-10-06
bump, I really need help with this please

---

### Post by Grenage on 2010-10-06
I'll help if I can.

Are you using an xorg.conf?  Try and open it in gedit:

```
gedit /etc/X11/xorg.conf
```

If so, please paste it here.

---

### Post by NekoMaster on 2010-10-06
This is my xorg.conf

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
	Driver	"fglrx"
EndSection

```

BTW my H and V refresh rates should be (H) 30-93KHz (V) 60-160Hz but ubuntu doesnt seem to know how to get that from my monitor

---

### Post by Grenage on 2010-10-07
It's possible that it's seeing them, they're just not listed in xorg.conf.  You can rule that out by using a custom xorg.conf; I have a guide [here]("http://www.grenage.com/xorg.html").

---

### Post by NekoMaster on 2010-10-07
> **Grenage said:**
> It's possible that it's seeing them, they're just not listed in xorg.conf.  You can rule that out by using a custom xorg.conf; I have a guide [here]("http://www.grenage.com/xorg.html").

I've tried multiple times editing my Xorg, Im on 9.04 now and I still have no luck, as it ignores anything I add (unless its an invalid command then it freaks out)

is there any programs I can get that will force a refresh rate?

EDIT : I tried your method and it still only displays at 60Hz. This is really starting to get on my nerves

---

### Post by soldier1st on 2010-10-07
are you using a VGA cable or a DVI as DVI limits your refresh rate to 60 htz even if your monitor/video card can do higher. DVI cables are White while VGA are Blue.

---

### Post by NekoMaster on 2010-10-08
> **soldier1st said:**
> are you using a VGA cable or a DVI as DVI limits your refresh rate to 60 htz even if your monitor/video card can do higher. DVI cables are White while VGA are Blue.

Im using VGA since the AOC 9glr is a VGA CRT Monitor (btw I already know the differnces between the both)

---

### Post by realzippy on 2010-10-08
*I tried your method and it still only displays at 60Hz.* 

..can you post your *current* xorg.conf then?

---

### Post by realzippy on 2010-10-08
doublepost deleted.something was wrong with the forum server  ;-)

---


---
title: "Change resolution to 800x600 16:9"
date: 2011-10-25
forum: General Help
---

### Post by abhishek_turbo911 on 2011-10-25
The present resolution options show me with 1024x600 (16:9) and 800x600 (4:3). I want 800x600 at 16:9. Can anyone please help me?

---

### Post by Vaphell on 2011-10-25
i think that 16:9 or 4:3 merely tells you that the resolution is widescreen/non-widescreen and that's it.
Besides why would you want a distorted picture?
Either way, try using that 800x600, if your video adapter stretches it to fill the whole panel you are good to go.

---

### Post by abhishek_turbo911 on 2011-10-25
> **Vaphell said:**
> i think that 16:9 or 4:3 merely tells you that the resolution is widescreen/non-widescreen and that's it.
Besides why would you want a distorted picture?
Either way, try using that 800x600, if your video adapter stretches it to fill the whole panel you are good to go.

Yes. On Win7 the widescreen works perfectly. But on Ubuntu, while keeping it on 800x600 it does not stretch entirely.

---

### Post by Vaphell on 2011-10-25
what video card is in your netbook? is there some configuration tool for video driver?

---

### Post by abhishek_turbo911 on 2011-10-25
> **Vaphell said:**
> what video card is in your netbook? is there some configuration tool for video driver?

It is Intel GMA3150. There was a config tool for Windows.

---

### Post by abhishek_turbo911 on 2011-11-04
Some help guys?

---

### Post by matt_symes on 2011-11-04
Hi

Open a terminal and type

```
xrandr --prop
```

Post the results back here.

Kind regards

---

### Post by abhishek_turbo911 on 2011-11-13
This is the code that comes up:

> 

abhishek@abhishek-laptop:~$ xrandr --prop
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 222mm x 125mm
	EDID:
		00ffffffffffff000daf251000000000
		3313010380160c780a0ac5925a569127
		20505400000001010101010101010101
		0101010101012c15006a415834206d48
		7d00de7d00000018000000fe004e3130
		314c362d4c30410a2020000000fe0043
		4d4f0a202020202020202020000000fe
		004e3130314c362d4c30410a2020009e
	BACKLIGHT: 7 (0x00000007)	range:  (0,7)
	Backlight: 7 (0x00000007)	range:  (0,7)
	scaling mode:	Full aspect
		supported: None         Full         Center       Full aspect 
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)


---

### Post by Mark Phelps on 2011-11-13
The attached link provides details about using xrandr:

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

First thing to do is issue the command to show the available video modes.  If it's not listed, there's nothing you can do.

---


---
title: "Nvidia drivers issues  fx5500"
date: 2009-09-07
forum: General Help
---

### Post by froggger on 2009-09-07
I have gone through a cuple different nvidia drivers and nvidia cards trying to find one that works for my purposes.

I had one that didn't work well and didn't fit my needs, one that worked perfectly and fit my needs, but had no heatsink, and this one which i think should work fine, but its not.

Its an nvidia fx5500 agp.  I have the 173 drivers installed and they installed correctly, but my resolution is pitiful.

The highest it will let me go is 640x480.  Even with no drivers i could get up to 800x600.

I don't know what to do, i've tried multiple versions of the drivers, with no luck.

Any ideas?

---

### Post by overdrank on 2009-09-07
> **froggger said:**
> I have gone through a cuple different nvidia drivers and nvidia cards trying to find one that works for my purposes.

I had one that didn't work well and didn't fit my needs, one that worked perfectly and fit my needs, but had no heatsink, and this one which i think should work fine, but its not.

Its an nvidia fx5500 agp.  I have the 173 drivers installed and they installed correctly, but my resolution is pitiful.

The highest it will let me go is 640x480.  Even with no drivers i could get up to 800x600.

I don't know what to do, i've tried multiple versions of the drivers, with no luck.

Any ideas?

Hi and what version of Ubuntu are you using? Have you tried using the nvidia settings to change the resolution? ```
gksu nvidia-settings 
```

---

### Post by froggger on 2009-09-07
jaunty 9.04.
and yes, i've tried nvidia settings, only options are auto, 640x480 and 320x240

---

### Post by froggger on 2009-09-07
bump...

---

### Post by froggger on 2009-09-08
bump

---

### Post by Japjeev on 2009-09-08
> **froggger said:**
> bump

please dont spam i had the same problem with same card 5500 fx all i did was install x server. and if that doesnt work download driver install it from terminal

---

### Post by overdrank on 2009-09-08
> **froggger said:**
> bump

Hi and can you post your xorg. ```
cat /etc/X11/xorg.conf
```

---

### Post by froggger on 2009-09-08
```
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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```

---

### Post by overdrank on 2009-09-08
Ok have you tried  [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by froggger on 2009-09-08
I just now did and i got to adding a new mode, but then i got an error.
```

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  18
  Current serial number in output stream:  18

```

Thanks for the help.
Shouldn't the driver do all this automatically?
Why isn't it?


I'll try this later, see if it does the trick.
[http://jrobbo.com/blog/?tag=fx5500](http://jrobbo.com/blog/?tag=fx5500)
and maybe this 
[http://ubuntu-helper.blogspot.com/2009/04/nvidia-geforce-fx5500-resolution-fix.html](http://ubuntu-helper.blogspot.com/2009/04/nvidia-geforce-fx5500-resolution-fix.html)

It turned out to be my crappy monitors fault.
Hooked it up to my LCD and it detected everything standardly

---

### Post by zero-n on 2009-10-01
I have tried many ways to solve this problem but it didn't work
finally i discovered that the problem is from my monitor so i change it with another to try it and it work well

---


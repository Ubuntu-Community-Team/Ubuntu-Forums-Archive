---
title: "Flickering screen"
date: 2009-11-12
forum: General Help
---

### Post by grenadecx on 2009-11-12
Okay, hope someone can shed some light on this.

After my upgrade from jaunty to karmic, my screen starts flickering random and I can press CTRL+ALT+F1 and back and it stops flickering. However, the textures looks completely messed up, I have relog for it to become normal again. These flickering are completely random, when I play a movie, gaming, or just surfing the web. So I thought it might be something from the upgrade, so I made a clean install, but the problem didn't go away.

I'm thinking that this could either be a driver issue OR it could be a bug in xorg. So I wonder if any else out there have experience any similar behavior. 

I'm having a Nvidia graphic card, Geforce GTX 260 and the nvidia driver 185.18.36.

Any response is appreciated.

---

### Post by upbeat.linux on 2009-11-13
I experienced the same issue with an upgrade to 9.10.  I had a custom xorg.conf that I overwrote and there was a bit of flickering and then what appeared to be dead pixels (various shades of red and orange) on the screen. I reset but it didn't go away.  Finally, I checked both my DVI cables and they were loose.  Tightening them up caused the pixels to go away and the flicker to stop.  

This might not help, but its a first step.

There's also a bug report filed by a few folks who were having the same issue:

[https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/443223](https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/443223)

Looks like it might be an issue with gtk+ as well.

---

### Post by upbeat.linux on 2009-11-13
This was also posted a few hours before yours:

[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

---

### Post by grenadecx on 2009-11-16
Thanks for your reply.
I was away during the weekend, so couldn't reply.

Anyways, I checked the first post, and that doesn't affect me at all. And then I checked the second one and it doesn't seem to affect me either, since my monitor is detected and has always been ever since Ubuntu 7.04. 

This issue is driving me crazy, it appears totally random, just happened a few minutes ago. I'm thinking about reverting to 9.04 that worked perfectly well for me, but it's kinda ridiculous.

---

### Post by Giblet5 on 2009-11-17
Have a look at one of the many [HOWTO]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145")s.

---

### Post by grenadecx on 2010-01-20
Okay, let me update. This wasn't solved after trying out this howto:

[http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145)

I have an Acer monitor labeled, AL1916W, when I went into menu, I found out it's HorizSync and VertRefresh, which was:

HorizSync:    55 Khz
VertRefresh:  59 Khz, but when I ran as in the example of the guide:
```

cvt 1440 900 60

```

I got this:
```

# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```

My screen still goes flickering/freezing at random times, my current xorg looks like this now:

[quote="xorg.conf"]
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    55
        VertRefresh  59
        VendorName   "Acer"
        ModelName    "AL1916W"
EndSection

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
[/quote]

I'm not sure what else I can provide. 

I can (sometimes) change session and back with CTRL+ALT+FX, but the textures are all messed up, however, if I restart an application that have textures messed up, it becomes normal. Sometimes my computer hangs at the beginning of these freeze/flickering, and I can't do anything else then hard-reboot.

---


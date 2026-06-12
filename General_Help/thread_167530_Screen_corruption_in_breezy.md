---
title: "Screen corruption in breezy"
date: 2006-04-28
forum: General Help
---

### Post by frank05 on 2006-04-28
I have a laptop with a radeon9600 graphics chipset. I have been trying to get a dual head set up since last summer but have had no sucess so far. This is because the display on the second monitor is always corrupted (i.e. the screen shimmers and tiny lines gradually appear). 
Until now I have thought the problem was with my xserver config however, I have noticed that I have the same problems when using the console (no x server). Could this mean there is some other way of fixing this? I've heard passing command line parameters to the kernel can help. Does anybody know where I can find documentation on this?

Thanks,

---

### Post by xgrendel on 2006-04-28
My experience with dual-head video cards is quite limited. I previously ran Xinerama and Mandriva and it too very little effort to get those cards to work. I did some reading on Google and there appears to be quite a few different threads  specifically regarding ATI cards and problems people have had. There was also a thread off of a bug listing on the Debian threads regarding a similar issue. I just used [google]("http://www.google.com/search?q=xserver+dual+monitors+radeon+9600&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial") to find some suggestions on it -there appear to be too many to go through and link here specifically.

---

### Post by djsroknrol on 2006-04-28
Hi Frank05...

try this link....I think it might help you...good luck with it...

[http://ubuntuforums.org/showthread.php?t=160499](http://ubuntuforums.org/showthread.php?t=160499)

---

### Post by BryanL0911 on 2006-04-28
Here is a bug report with fix that I found yesterday but have not had a chance to try on my own laptop yet....


[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/26341](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/26341)

---

### Post by frank05 on 2006-04-28
Right! Tad embarrasing this :$ .  Getting rid of the screen corruption was a simple matter of rebooting *with* the external monitor plugged in. :D The next hurdle was stopping the xserver from simpley swaping the laptop screen for the external monitor. This was done by specifying the following in the device section.
```

#(using djsroknrol server config)
Option "MonitorLayout"              "LVDS, CRT"

```

LVDS being the laptop screen. By default it takes the CRT/LCD to be the primary and the TV to be the secondary (which it probably couldnt use anyway :P ) .

Anyway I'm more than happy with my dual screens. In fact its better than windows! In linux I can run my external monitor at a higher resolution and refresh rate.

Where it not for the fact I have collegues who love VS.NET i'd delete my windows partition now! :D

Thanks all!

---


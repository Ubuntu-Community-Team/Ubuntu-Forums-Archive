---
title: "ubuntu still buggy for people with tablet laptop and external monitor"
date: 2010-10-10
forum: General Help
---

### Post by warakawa on 2010-10-10
I tried ubuntu 10.04 then uninstalled when back to windows 7 due to various difficulties. 

I was all excited about 10.10 hoping that ubuntu developers would have fix some of the serious bugs that presented in 10.04. 

I have a tablet pc with a two external monitors (U2711 2560x1440 and another 1920x1200), in Windows 7 I can turn on and turn off external monitors with ease however, in Ubuntu 10.10 it is extremely difficult, if I want to turn off one monitor from two monitors or change a from one monitor to another monitor, Ubuntu will most of the time freeze completely, giving me two blank screens and then I have to restart my laptop, Ubuntu's 30 second return to previous setting doesn't always work. 

On the topic of multiple monitors, Ubuntu's monitor perimeter is weird, it let's the mouse go off the monitor, some times I can not get to my application because I have accidentally drag the application off the monitor. 

Ubuntu 10.10 still have no good support for tablet pc users, windows 7 have everything for tablet user out of the box, (all the buttons on the stylus works, the on screen virtual keyboard/writing pad, etc). Ubuntu has nothing for tablet out of the box.

---

### Post by Favux on 2010-10-10
Hi warakawa,

You should be able to get almost everything on your X200t working.  With Maverick (10.10)'s default xf86-input-wacom 0.10.8 your tablet should be working out of the box.

In terms of the multiple monitors that isn't really Ubuntu.  That's your video chipset, video drivers, and Xorg's Xserver.

---

### Post by warakawa on 2010-10-10
how come multiple monitors work flawlessly in Windows 7?

---

### Post by Favux on 2010-10-10
Because the video chipset manufacturers put in the developer resources necessary.  In other words they spend the money.  Again not so much a Windows 7 thing, it's more what the video manufacturers do.  For example AMD/ATI only recently started releasing some of their specifications to the open source community.

Is it an Intel chipset you have?
```
lspci | grep VGA
```

---

### Post by Ralph Corderoy on 2010-10-11
Or better still, what's the output of "lspci -nn | grep VGA" as that will give us the PCI ID numbers too.

[http://www.thinkwiki.org/wiki/Category:X200](http://www.thinkwiki.org/wiki/Category:X200) suggests it may have Intel Graphics Media Accelerator 4500MHD?

---

### Post by Mark Phelps on 2010-10-11
> **warakawa said:**
> Ubuntu 10.10 still have no good support for tablet pc users, windows 7 have everything for tablet user out of the box, (all the buttons on the stylus works, the on screen virtual keyboard/writing pad, etc). Ubuntu has nothing for tablet out of the box.

You have my sympathies.  Also running Win7 on a tablet PC, and like you, am surprised that EVERYTHING works -- right out of the box!

My tablet PC has not worked well with Ubuntu since they upgraded to 8.10.

So, good luck with getting everything working.

---

### Post by dino99 on 2010-10-11
what i can say: watch logs to find errors and googled around them.
Sometimes this command help:

sudo update-usbids && sudo update-pciids

---


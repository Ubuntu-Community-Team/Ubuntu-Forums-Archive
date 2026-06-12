---
title: "Graphics problem after update"
date: 2010-02-24
forum: General Help
---

### Post by PredatorOC on 2010-02-24
If there is one thing I've learned over the years of using Ubuntu, it's a healthy fear of updating Ubuntu.

Once again, after updating, something has gone wrong with the graphics. When starting the computer, the loading screen shows up, but the login screen is a mangled mess at the top of the screen. And after trying to automatic fix for graphics problems (xfix), the magled login screen simply vanishes after a few flickers.

At this point in the past I've simply reinstalled, but thought I'd ask if there was something to spare me this hassle.

I'm using 9.04 and the graphics card is ATI Radeon HD 4550.

Thanks in advance.

---

### Post by Mark Phelps on 2010-02-24
You didn't mention if you were using the ATI drivers (fglrx), but I'm presuming you were.

As to why an update should suddently bork your display, last time I used restricted drivers, I did read about kernel updates hosing the drivers.  So, if it was a kernel update, that might explain what happened to you.

If you installed from the 9.04 original CD, that's a pretty old version of the ATI drivers (Catalyst 9.2? 9.3?).  A newer version is liable to give you better results.

Since you have a 45XX card, I don't know if you'd benefit from the latest Catalyst 10.x drivers, but you should be able to use Catalyst 9.11 (that's the latest 9.xx version -- as far as I know).

---

### Post by tom4everitt on 2010-02-24
What about booting from an older kernel?

---

### Post by PredatorOC on 2010-02-24
Yes, it was a kernel update and I've used the drivers from ATI's site.

I tried booting from the older kernel options on grub, but the result is the same.

I tried messing around with xorg.conf to use vesa drivers, but that didn't do anything. I also tried X -configure and dpkg-reconfigure, but nothing has helped thus far.

---


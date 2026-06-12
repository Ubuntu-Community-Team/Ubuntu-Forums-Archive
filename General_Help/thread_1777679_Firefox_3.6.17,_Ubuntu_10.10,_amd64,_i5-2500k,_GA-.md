---
title: "Firefox 3.6.17, Ubuntu 10.10, amd64, i5-2500k, GA-HA65M-UD3H-B3 (rev. 1.0)"
date: 2011-06-08
forum: General Help
---

### Post by helloicanseeu on 2011-06-08
hi, 

from time to time, firefox causes my system to hang, i always recover by presssing ALT+PrtScr+K,
login again, then everythings fine, until firefox acts up again

firefox hangs when i load large images, sometimes it doesnt,
but everytime it hangs, large images on a single tab will be involved some way.

my guesses are either 
1.bad firefox settings in config (involving images?)
2.bad firefox addons (i do have quite a list active here)
3.flash-addon (i using the experimental 64-bit addon herehttps://launchpad.net/~sevenmachines/+archive/flash)
4.bad BIOS settings (BIOS memory settings are set to Turbo (given choices of NORMAL/TURBO/EXTREME)
5.bad memory (using normal Kingston 1333, 4gx2 pair here)
6.buggy intel drivers (is that possible)?

currently too lazy to test it out, will love to have input from those who had the same experience/or solved the problem

---

### Post by mastablasta on 2011-06-08
my guesses are either 
1.bad firefox settings in config (involving images?) **NO**
2.bad firefox addons (i do have quite a list active here) **YES**
3.flash-addon (i using the experimental 64-bit addon herehttps://launchpad.net/~sevenmachines/+archive/flash) **YES**
4.bad BIOS settings (BIOS memory settings are set to Turbo (given choices of NORMAL/TURBO/EXTREME) **NO**
5.bad memory (using normal Kingston 1333, 4gx2 pair here) **NO (unless you get issues and crashes with other progs as well)**
6.buggy intel drivers (is that possible)? **YES for graphics card, but likely no**.
 
 
try removing and installing firefox fresh and see it it helps. then you know it's one of the addons.

---

### Post by helloicanseeu on 2011-06-08
hmm .. maybe its time to change browser ...

---

### Post by lovinglinux on 2011-06-08
I would bet on graphics driver.

I would recommend blocking unnecessary flash content with [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/"), [optimizing your Firefox databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization") and [checking if you have problematic extensions]("http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting"). Trying a clean profile wouldn't hurt either.

I also recommend [trying Firefox 4]("http://ubuntuforums.org/showthread.php?t=1712247"), which is a lot faster than Firefox 3.6.x.

---

### Post by helloicanseeu on 2011-06-08
> **lovinglinux said:**
> I would bet on graphics driver.


are the ubuntu 10.10 intel graphic drivers for sandy bridge really that bad?
i know ubuntu's a bit slow catching up,
there's no ubuntu drivers for this Etron EJ168 usb 3.0 chipset,
maybe it'll be like 6mths before we see one ...

> **lovinglinux said:**
> 
I would recommend blocking unnecessary flash content with [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/"), [optimizing your Firefox databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization") and [checking if you have problematic extensions]("http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting"). Trying a clean profile wouldn't hurt either.

 hmm ... i tried deleting the auto-generating .dat files(compreg.dat  pluginreg.dat  xpti.dat) in profiles directory, doesnt help.

okie, will try optimizing FF databases, looks fun.

checking for problematic extensions, hmm ... very tough detective work .... i'll skip for now :), see how it goes ... should be the last option.

trying clean profile .... hmm ...maybe

before upgrading to i5-2500k, i never had this problem of FF hangup, but what can i do about the intel graphics drivers in ubuntu 10.10, the only thing is to upgrade to 11.04.
i'm actually waiting for hidpoint to support 11.04 before i upgrade to 11.04,
using logitech wireless stuff here.

> **lovinglinux said:**
> 
 I also recommend [trying Firefox 4]("http://ubuntuforums.org/showthread.php?t=1712247"), which is a lot faster than Firefox 3.6.x.

  hmm ... if the cause of the hangups are in the graphics driver, why would using a later version of firefox help? i expect ff4 to also have the same kind of bugs there, should be related to the way firefox handles images, from 3.6 to 4.0, i dont expect drastic change in image handling routines.

i'm more like waiting for the extensions to catch-up with firefox, with regard to latest versions. stablity/persistence is preferred than speed in ubuntu.

Lastly, thanks for the advice and input.

---

### Post by helloicanseeu on 2011-06-10
now using firefox 4, still get the same kind of problem, still using alt-prtscr-k to regain control,

problem should lie with the intel graphics driver

---

### Post by linuxinstalledfromhdd on 2011-06-10
Did you guys try this:

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

---

### Post by helloicanseeu on 2011-06-11
> **linuxinstalledfromhdd said:**
> Did you guys try this:

[http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/](http://cinderbox.net/2011/03/22/flash-aid-addon-for-firefox-automatically-detects-best-flash-version-for-your-system/)

wait, are u also facing this problem too?

now,i fiddling with the various image, mem parameters in about:config,
mostly the integers, using 4x or so the default value,
to see it this image problem hang can be avoided,
will update if problem resolved,
if so, means that the intel graphics or experimental flash plugin, has nothing to do with it. if so, better it will be.

i remember using opera mobile on samsung b7610, a couple of web pages wouldn't load unless some numeric parameters was increased, say doubled or so.

---

### Post by helloicanseeu on 2011-06-13
update, 

disabled "Tab Mix Plus" addon
used instead "Tab Utilites", 2nd most popular addon for tabs
appears to soothe Firefox 4 a lot,
this seems to be the cause of all these hangups.

---


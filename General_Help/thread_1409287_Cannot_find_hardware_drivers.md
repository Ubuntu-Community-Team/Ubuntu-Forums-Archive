---
title: "Cannot find hardware drivers"
date: 2010-02-17
forum: General Help
---

### Post by merlync70 on 2010-02-17
I have an issue that I suspect is probably not a big deal to fix, but since I am fairly new to Linux I haven't been able to resolve it.  I will start with the problem, then give some history to how the problem started.

PROBLEM: RIGHT CLICK DESKTOP >> CHANGE DESKTOP BACKGROUND >>TAB TO VISUAL EFFECTS >> TRY TO SELECT "NORMAL" OR "EXTRA"  >> WINDOW OPENS THAT SAYS "DESKTOP EFFECTS COULD NOT BE ENABLED" .
... ALSO ...
SYSTEM >> ADMINISTRATION >> HARDWARE DRIVERS >> "NO PROPRIETARY DRIVERS ARE FOUND ON THIS SYSTEM"

HISTORY:
My Ubuntu WAS working perfectly.  I started to tweak with the eye candy. "Advanced Desktop Effects Settings (ccsm)." As I was reading some of the forums, I also thought I would give KDE a try and add it to my system.  I was experimenting (so I don't know what exactly I was modifying) when at some point I noticed that in the upper right hand corner of my windows (where "minimize window, maximize window and close window buttons" exist), each time I went to click on the close window button, my system froze and I had to do a hard reboot.  At that point, I uninstalled all things KDE.  Still had the same issue.  Then I uninstalled ccsm.  

At this point, the maximize, minimize and close buttons were GONE!!  I finally figured out, I had to RIGHT CLICK DESKTOP >> CHANGE DESKTOP BACKGROUND >>TAB TO VISUAL EFFECTS >> SELECT "NONE"
This returned my system back to a useable state with the max, min and close buttons.  Then I tried again to enable the effects, and suddenly my max, min, close buttons again disappeared.  I also got a window that was searching for drivers.  None could be found.  I had to then turn effects off again. 

After that, Ive been trying to completely uninstall and reinstall: drivers, KDE, ccsm, hardware drivers (jockey-gtk and jockey-kde).  I tried installing each of them seperately, together, and in various combinations and now it seems like the more I try the worse it gets (before, it would search for drivers... now it just tells me "desktop effects could not be enabled"

I know there is probably an easy fix to restoring my drivers... but I can't figure it out.  It would be easy to just reinstall... but then I gotta go back to my IT person to add the network key at my work and redo all my settings.

Any help would be most appreciated.  Thanks!

By the way: Ubuntu 9.10 64-bit on a Dell Inspiron 1420 laptop

---

### Post by SyntheticXTC on 2010-02-17
I have an ATI x1950 pro card that turned legacy not too long ago and now with 9.10 im not getting any proprietary video drivers at all anyway.  When I try to use the desktop effects it is telling me the same error that you are getting. So there may be a way to compile the drivers by hand but I have not figured out how to get this done yet.

Good Luck.

PS: Maybe give us the name of the video card also so we can trouble shoot, being its a laptop it may just be a chipset I guess.

---

### Post by merlync70 on 2010-02-17
> **SyntheticXTC said:**
> I have an ATI x1950 pro card that turned legacy not too long ago and now with 9.10 im not getting any proprietary video drivers at all anyway.  When I try to use the desktop effects it is telling me the same error that you are getting. So there may be a way to compile the drivers by hand but I have not figured out how to get this done yet.

Good Luck.

PS: Maybe give us the name of the video card also so we can trouble shoot, being its a laptop it may just be a chipset I guess.

That would certainly be annoying, having to recompile the drivers. Fortunately for my situation, I know the drivers exist and work... because the were fine yesterday before I started tinkering. 

According to wikipedia, my setup has"integrated Intel GMA X3100 graphics or nVidia GeForce 8400M GS"
[http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1420](http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1420)

---

### Post by philinux on 2010-02-17
> **merlync70 said:**
> That would certainly be annoying, having to recompile the drivers. Fortunately for my situation, I know the drivers exist and work... because the were fine yesterday before I started tinkering. 

According to wikipedia, my setup has"integrated Intel GMA X3100 graphics or nVidia GeForce 8400M GS"
[http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1420](http://en.wikipedia.org/wiki/Dell_Inspiron#Inspiron_1420)

What exactly did you tinker with.

A tutorial from somewhere?

---

### Post by merlync70 on 2010-02-17
> **philinux said:**
> What exactly did you tinker with.

A tutorial from somewhere?

I was messing with desktop effects on ccsm and the KDE equivalent.  Settings such as Cube, reflections, etc.  It all started when I read that someone prefered KDE, so I thought I would install it and check it out.

---

### Post by philinux on 2010-02-17
> **merlync70 said:**
> I was messing with desktop effects on ccsm and the KDE equivalent.  Settings such as Cube, reflections, etc.  It all started when I read that someone prefered KDE, so I thought I would install it and check it out.

This might help with ridding you of kde.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Mark Phelps on 2010-02-17
> **SyntheticXTC said:**
> I have an ATI x1950 pro card that turned legacy not too long ago and now with 9.10 im not getting any proprietary video drivers at all anyway.  When I try to use the desktop effects it is telling me the same error that you are getting. So there may be a way to compile the drivers by hand but I have not figured out how to get this done yet.

That won't do you any good -- because there is a basic incompatibility between the older ATI drivers and the Xorg versions used in Ubuntu 9.04 and 9.10. Essentially, the "older" drivers won't work with the "newer" Xorg.

You would have to downgrade the XServer as a side-effect -- and then, you have to lock the packages to prevent upgrades -- and then, you're running with an obsolete version of the Xserver.

There are threads on HOW you can do this.  If you search, you will find them.  But look at where you end up!

In addition, the "newer" ATI drivers simply won't work with the "legacy" cards -- no matter how you compile them.  The last driver that WOULD work with your card is Catalyst 9.3 -- and that's one of the "older" drivers mentioned above.

---


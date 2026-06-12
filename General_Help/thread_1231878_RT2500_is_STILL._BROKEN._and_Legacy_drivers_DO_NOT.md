---
title: "RT2500 is STILL. BROKEN. and Legacy drivers DO NOT COMPILE."
date: 2009-08-05
forum: General Help
---

### Post by Furyhunter on 2009-08-05
**This is the third time I have asked this on these forums in the past week.**  I am on the brink of *abandoning Ubuntu* because the alleged *awesome support* is a complete *fallacy*.

The RT2500, after reading every guide and tutorial to fix the issues in Ubuntu (sudo iwconfig wlan0 rate 54M, using wicd instead of NetworkManager, using rutilt instead of wicd, compiling the legacy drivers), **still fails to work.**  Modprobe won't even detect the legacy driver that `make install` clearly states is installed.  The "Hardware Drivers" panel doesn't see any driver.  Following the README included in the legacy driver source tarball yields *nothing*.  Setting the tx rate to 54M manually lasts all of about five seconds before it decides to revert to something like **forty bytes per second**.  NetworkManager, wicd, and RutilT all do exactly the same thing - nothing.

I am getting sick and tired of this crap.  It was broken 5 months ago, it is still broken, and I assume it will never get fixed.  How can an operating system like this tout about its constant reliability when it can't even fix something it broke when it imported the serialmonkey driver in to the kernel line?  Most unreliable thing I've ever used.

---

### Post by 3rdalbum on 2009-08-05
Ubuntu works well for most people. I hear good things about the new version of Fedora.

---

### Post by CatKiller on 2009-08-05
> **Furyhunter said:**
> **This is the third time I have asked this on these forums in the past week.**  I am on the brink of *abandoning Ubuntu* because the alleged *awesome support* is a complete *fallacy*.

That's a nice way to get people on your side to help you, isn't it?

---

### Post by techstop on 2009-08-05
> **Furyhunter said:**
> <SNIP assorted whining>

> **CatKiller said:**
> That's a nice way to get people on your side to help you, isn't it?

Exactly. These forums are a *community*, people helping out each other. Nobody here *owes* you anything, Furyhunter.

There are plenty of wireless cards available that work fine out of the box. You could save yourself some headaches just by buying one that works.

---


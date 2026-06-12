---
title: "Flash/Java eating my system resources?"
date: 2009-08-13
forum: General Help
---

### Post by Geezle on 2009-08-13
I'm working with a fairly fresh install of Jaunty, and I noticed that on certain web sites, particularly ones with a lot of animated ads, eat up to half of my CPU resources.

I'm not sure which flash handler I'm using, but could this be the problem?  Would changing my flash program affect this?  

How would I go about changing my program to try to figure this out?

---

### Post by Geezle on 2009-08-14
OK, so it's definitely my Flash.  I've tried the Adobe flash player, the SWF player, and gnash, and all seem to use up a LOT of my system resources.  It didn't do this before I had to reinstall Ubuntu (with a new MoBo) so I'm quite confused.  

It has gotten to the point that sometimes Firefox will just grey out and not respond for a while and use up all my system resources.  If I go into the System Monitor and end gnash then my resource usage seems to go back down to normal.  

What am I missing?!

---

### Post by XCan on 2009-08-14
You're probably missing flashblocker, or a simply adblock to remove the pesky flash ads. Besides making sure that you are using the right flash version, i.e., 64-bit for 64-bit OS, there really isn't much to do. Flash is inherently crappy coded.

---

### Post by lovinglinux on 2009-08-14
Flash sucks and some javascript web sites can eat your CPU too.

Use [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865), [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433).

Additionally, check the Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---


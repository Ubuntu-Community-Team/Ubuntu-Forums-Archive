---
title: "sudden drop in sound quality"
date: 2011-03-20
forum: General Help
---

### Post by dre12b on 2011-03-20
About a month ago I uninstalled Rhythmbox and installed Banshee to give it a testspin on my 10.10 install.  My sound quality has deteriorated significantly, not only for music played in Banshee but also for VLC or any other application.  I'm not 100% sure that it happened when I installed Banshee, but it was the only change made other than normal updates.  The overall volume on my laptop has diminished and the sound becomes fuzzy and distorted if over 50% or so.

This is probably something silly, but I'm not sure what angle to go at the problem from.  Any suggestions on where to start?

---

### Post by cottfcfan on 2011-03-20
Try reinstalling Rhythmbox. It may be that you also deleted some needed codecs with it.
I've seen somewhere on the Forums not to delete anything that comes with the standard install. It has a habit of breaking things.
Also if you haven't already install the ubuntu-restricted-extras package. That may help.

---

### Post by dre12b on 2011-03-20
Reporting back here...a bit sheepishly.  The solutions was one part strange Ubuntu behavior to two parts my own silliness.  

The short of it: I had reduced the volume using the hardware buttons on my thinkpad and then forgotten about it.  Increasing the volume using the hardware buttons (which I usually ignore) fixed the "problem".

The longer story is that for some reason, the OSD for volume, screen brightness, and muting using the hardware keys on the thinkpad used to work on Ubuntu thanks to a tpb (thinkpadbutton) package in the repositories.  At some point between 9.10 and 10.10 these stopped working, so I had no idea the hardware volume, which is distinct from the volume slider in the panel, was set very low.  I followed the instructions from davidovp [http://ubuntuforums.org/showpost.php?p=9591408&postcount=34](http://ubuntuforums.org/showpost.php?p=9591408&postcount=34) to reenable the OSD.

By the way, thanks for the suggestions.  I tried reinstalling rhythmbox to no avail before discovering the actual problem.

---


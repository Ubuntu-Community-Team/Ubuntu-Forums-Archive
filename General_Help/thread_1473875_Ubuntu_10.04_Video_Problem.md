---
title: "Ubuntu 10.04 Video Problem"
date: 2010-05-05
forum: General Help
---

### Post by vwbug on 2010-05-05
Just "upgraded" (if you can call it an upgrade:lolflag:) from 8.04 to 10.04.  Had problems with the video even while booting from the CD as the screen would go blank.  Anyway worked around that and installed 10.04.

Now every time I shut down or reboot I loose the panel! With no panel I did a alt+F1 to bring up the menu, went to the NVIDIA x server settings and change to 1024x768 and my panel is back. Go back and change to 1280x960 and everything is OK until I shut down or reboot.  This setting has worked fine on Hardy, even without the NVIDIA drivers.

Any help would be very much appreciated.  Thanks

---

### Post by no2498 on 2010-05-05
it is not a Video Problem

you need the settings manager for your monitor 
monitor settings
monitor settings linux

---

### Post by vwbug on 2010-05-05
> **no2498 said:**
> it is not a Video Problem

you need the settings manager for your monitor 
monitor settings
monitor settings linux

Could you elaborate? The Nvidia X server program shows the correct monitor. The "Monitor" program that is in Ubuntu is not used when the Nvidia program is installed.  Not sure to what you refer.

---

### Post by vwbug on 2010-05-05
Well whatever the problem was, it was fixed by doing an update.
A Bug maybe?

---

### Post by no2498 on 2010-05-06
lol vwbug

glad its working now

---

### Post by vwbug on 2010-05-06
Seems all this is related to the NVIDIA drivers.  The panel is there now, but I can't right click on my desktop and any files downloaded to the desktop don't show up.  If I remove the drivers the desktop is OK but I can only get 1024x764 resolution with the supplied Ubuntu drivers. Really don't know what to do at this point. A hammer maybe???

I didn't use a hammer, but I did install 9.10.  Works great.  I don't know, maybe because I have an old CRT monitor the drivers didn't support it.

There are subtle differences between 9.10 and 10.04 that I didn't like. Never could figure out how to login as root, my desktop not working, panel disappearing, For me 10.04 was "Vista", well not THAT bad.  If I ever get a new video card and monitor MAYBE I'll go to 10.04.

---


---
title: "tv only display"
date: 2010-10-18
forum: General Help
---

### Post by emada on 2010-10-18
So i have a ubuntu box hooked up to my tv and while i have my monitor plugged in and on during boot up it works fine but if i try to boot with the monitor off it fails to load and i get a error message about ubuntu needs to go into a low graphics mode. I guess this is due to x trying to load xorg.conf.failsafe how can i stop this so i can use it w/o a monitor?

---

### Post by efflandt on 2010-10-19
What kind of TV is it, how is it connected to your computer, and what video drivers are you using?  If it is an old SD TV connected with composite or S-Video it is going to be low resolution anyway.

VGA often cannot determine resolution of the display and may just come up with a list of what it considers standard video modes (which if using default video drivers you can select from System > Preferences > Monitors).  Or with standard drivers you can use xrandr to temporarily add modes.  DVI or HDMI would usually work best.

Even old computers with video that I thought was pre-widescreen worked with VGA on an early 1280x720 LCD HDTV (which supports 4:3 modes up to 1280x1024).  The Monitors window did not list that native mode, but 1360x768 worked even though nothing in the HDTV manual mentioned that mode.  Whenever I connected it with DVI, X automatically recognized its native 720p resolution.  Likewise X would recognize the native resolution of a 1080p HDTV connected DVI to HDMI.

---

### Post by emada on 2010-10-19
> **efflandt said:**
> What kind of TV is it, how is it connected to your computer, and what video drivers are you using?  If it is an old SD TV connected with composite or S-Video it is going to be low resolution anyway.

VGA often cannot determine resolution of the display and may just come up with a list of what it considers standard video modes (which if using default video drivers you can select from System > Preferences > Monitors).  Or with standard drivers you can use xrandr to temporarily add modes.  DVI or HDMI would usually work best.

Even old computers with video that I thought was pre-widescreen worked with VGA on an early 1280x720 LCD HDTV (which supports 4:3 modes up to 1280x1024).  The Monitors window did not list that native mode, but 1360x768 worked even though nothing in the HDTV manual mentioned that mode.  Whenever I connected it with DVI, X automatically recognized its native 720p resolution.  Likewise X would recognize the native resolution of a 1080p HDTV connected DVI to HDMI.

its a old tv connected via composite and yeah i know the res will be low and thats ok, i just want it to start with out a monitor and with out it trying to reconfigure X. im using this motherboard: [http://www.jetwaycomputer.com/J7F2.html](http://www.jetwaycomputer.com/J7F2.html) and ubuntu 10.04

---

### Post by emada on 2010-10-20
anyone have any ideas?

---


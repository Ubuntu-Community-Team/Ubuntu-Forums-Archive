---
title: "please help too slow"
date: 2010-06-09
forum: General Help
---

### Post by martinipunk on 2010-06-09
Performed a fresh install last night after switching from windows 7. My problem is ubuntu (10.4)  is running incredibly slow. To do installs the cursor changes to the thinking icon for about thirty seconds then back and nothing happens for several minutes. system monitor says everything is idle and no processing is happening. one of my installs said that i lacked the required processor power to run, and its a pretty low requirement program.

several of the programs were installed through wine, however the problem still occurs with native programs, and administrator programs as well. Boots up and shuts down at normal speed.

also i cannot find any system information to see what drivers etc are installed or identified, when i pull up the update drivers tool it only displays the video driver says its running (but during initial update stated that it was the incorrect or out of date driver.)

amd phenom II x4 955 black edition
msi 790fx-gd70
8g ram
radeon 5850

---

### Post by Mark Phelps on 2010-06-09
> **martinipunk said:**
> Performed a fresh install last night after switching from windows 7. My problem is ubuntu (10.4)  is running incredibly slow. To do installs the cursor changes to the thinking icon for about thirty seconds then back and nothing happens for several minutes.
Installs using Software Center provide nearly no feedback.  So, while it may look like nothing is happening, behind the scenes, a LOT is happening.
>  one of my installs said that i lacked the required processor power to run, and its a pretty low requirement program.
We're not mind readers, here.  If you want help, you need to provide some details, like -- which program?

> several of the programs were installed through wine
Personal opinion is that Wine is a major kludge that works poorly at best.  IF you're so locked into MS that you have to use Wine, you're really better staying with Win7 -- EVERYTHING will work there; only SOME things will work in Wine, and many of them, very poorly.

>  ... however the problem still occurs with native programs, and administrator programs as well. 
Once again, not mind readers, here,  Which "native programs"?

>  ...also i cannot find any system information to see what drivers etc are installed or identified
This is NOT MS Windows, where the first thing you do after an install is hunt down and install all your needed drivers.  In Linux, this is done automatically for you during the installation.

So, unless you want to have ATI-specific hardware drivers, there is really nothing you need to install.

And, in that case, you should install the drivers that the Hardware Drivers is offering you, not go hunting around for drivers on your own. If it's not offering you any, that's a different problem.

---

### Post by martinipunk on 2010-06-09
Quote:
one of my installs said that i lacked the required processor power to run, and its a pretty low requirement program. 
We're not mind readers, here. If you want help, you need to provide some details, like -- which program?
world of warcraft.
 
several of the programs were installed through wine Personal opinion is that Wine is a major kludge that works poorly at best. IF you're so locked into MS that you have to use Wine, you're really better staying with Win7 -- EVERYTHING will work there; only SOME things will work in Wine, and many of them, very poorly.
 
i have little use for wine, maybe a few programs at most. however i could find no software support for specific hardware so i was attempting to run amd overdrive in wine, as well as a logitech keyboard interface, and (ms) mouse interface. also wow. i found counterparts for the keyboard and mouse.
 
... however the problem still occurs with native programs, and administrator programs as well. Once again, not mind readers, here, Which "native programs"?
 
openoffice, rythmbox, movieplayer, system testing (watched the bar bounce back and forth for a half hour before killing it), firefox (mostly unresponsive during operation.) the point was pretty much EVERYTHING accross the board is running abnormally slow.

---

### Post by lavinog on 2010-06-09
Are you running 32 bit ubuntu or 64bit?
Do you have desktop effects enabled?
What does your memory usage look like.
post the output of **free -m** (in a terminal)

also post the output of dmesg (use code blocks please...see my sig for more info)
dmesg might give some hints to what is going on with the kernel.

Also are you using the standard ubuntu install (not ubuntu studio or a realtime kernel)

---


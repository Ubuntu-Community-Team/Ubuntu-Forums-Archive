---
title: "Dual monitor problems"
date: 2006-06-18
forum: General Help
---

### Post by theswortz on 2006-06-18
I'm using kubuntu dapper and I have an ati graphics card. Anyway I was trying to setup dual monitors, one being my main monitor, the other being my tv. When I tried setting it up in kubuntu, everything was blurry on the tv. then I tried setting it back to the way it was and now kubuntu doesn't show anything on my monitor and it will show the garbled screen on my tv. The problem is that I can't login to kubuntu now because I can't see what's on the screen when it boots up. Can anyone tell me how to fix this so I can go back to normal. Also if someone knows of how I'm supposed to setup dual monitor with an ATI card, I would like to find out. Thanks.

---

### Post by RudolfMDLT on 2006-06-18
Hi there!

Boot into recovery mode, logging in as root would be helpful, and reset your ATI drivers to there initial state:

aticonfig --initial 

Then when your display does work, on KDE's terminal, type aticonfig and press enter. A huge list will appear of possible commands. I believe that there is a preset list of initial commands right at the end for running dual display.

Cheers

---

### Post by theswortz on 2006-06-18
I was not able to reset the driver. when I ran aticonfig --initial, it said command not found.

---

### Post by theswortz on 2006-06-19
I was able to restore everything by using a backup version of xorg.conf.  Since there is no aticonfig program, does this mean that I don't have the ati graphics driver installed?

---

### Post by RudolfMDLT on 2006-06-19
Sorry for only getting back to you now.

Okay, firstly in the console. run fglrxinfo, this will output what driver you are running. If it says something about mesa(which I think it will) the you have to first install the ati drivers.

[http://www.ubuntuforums.org/showthread.php?t=195845](http://www.ubuntuforums.org/showthread.php?t=195845)

The above post should help.

How did you try and enable the dual monitors? through Catalyst or through text base commands?

---

### Post by theswortz on 2006-06-20
the fglrxinfo output says:
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I'm gonna try installing the ati driver now. When I tried setting up the dual monitors, I went through the system settings in KDE.

---

### Post by RudolfMDLT on 2006-06-20
[QUOTE=theswortz]the fglrxinfo output says:
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I'm gonna try installing the ati driver now. When I tried setting up the dual monitors, I went through the system settings in KDE.[/QUOTE]

You need the ATI Drivers inorder to run dual display. Good luck, these ati cards are a right pain in tha but install! I'll check back here later to see if you had any problems...

---

### Post by theswortz on 2006-06-20
I got the driver installed with no problems. Thanks for the link. I tried setting up the dual monitor with it and it wasn't working the way I wanted to. I tried using the display settings of the system settings in kde to set it up, but I don't think its gonna work that way. When I set it to extended and set both the tv and monitor to the same resolution, the monitor has to scroll the display to show all of it. The tv doesn't have to scroll because the resolution is fitted to the tv, but I obviously don't want it like that. I was looking at the aticonfig command to see what options it had and it says something about a dual head display. I'm not by my computer now, but I'm gonna try that next when I can. Thanks for the help so far though.

---

### Post by RudolfMDLT on 2006-06-21
Great!

You won't believe how many people struggel for days to get there cards working!

---

### Post by ngakalden on 2007-12-30
theswortz: I am having the same situation you were at the time of this post...ATI driver on laptop, wanting to dual screen to my TV, but when I do, the resolution on my laptop downgrades, and I have to scroll. Did you eventually get this to work? If so, what steps did you take?

Thanks!!

---


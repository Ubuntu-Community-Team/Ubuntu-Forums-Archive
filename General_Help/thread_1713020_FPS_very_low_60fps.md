---
title: "FPS very low 60fps"
date: 2011-03-23
forum: General Help
---

### Post by trumpetmaster1 on 2011-03-23
I have a feeling that my video card is not working how its suppose to be. i installed the video card driver and all but i only get 60fps. do you know why? if so, can you show me whats wrong with it.

i am running-
ubuntu 10.10
ati radeon 9550
1gig of ddr ram
amd athlon xp 2600

---

### Post by pqwoerituytrueiwoq on 2011-03-23
it could be caped at 60
probably a sync to vblank option
ex there is no reason to generate 600 frames a seconds if only 60 can be displayed

---

### Post by trumpetmaster1 on 2011-03-23
> **pqwoerituytrueiwoq said:**
> it could be caped at 60
probably a sync to vblank option
ex there is no reason to generate 600 frames a seconds if only 60 can be displayed

so what can i do to make my fps to go faster? a new monitor?

---

### Post by Krytarik on 2011-03-23
Hi trumpetmaster1, do you actually know what 60 FPS means? It means that 60 images (frames) are getting display in a second, **F**rames **P**er **S**econd.
Also see here: [http://en.wikipedia.org/wiki/Frame_rate](http://en.wikipedia.org/wiki/Frame_rate)

Your initial assumption was right, that the FPS rate is capped at the refresh rate (Hz) of the used monitor. For example, I'm using an CRT, and in order to have no flicker effect I'm running it at 85 Hz. So, as the result the calculated FPS rate when running "glxgears" (as you mentioned it) variates near 85 Hz.

So, if you need to have a higher FPS rate in order to have a more fluent video when running games, for example, you could try to increase the refresh rate of your monitor via "System -> Preferences -> Monitors" (since I know that you're running the ATI OSED). If that isn't possible, it could either be that your monitor indeed doesn't support a higher refresh rate, or you need to use "xrandr" to add/choose the desired video mode:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

Greetings and good luck!

---

### Post by amauk on 2011-03-23
The rate at which frames are sent out of the graphics card is (usually) locked to the monitor's refresh rate

There is absolutely no point in shoving frames out faster than your display can handle

Most LCD monitors have refresh rates of 60Hz, therefore your graphics card will lock in on 60 FPS

---


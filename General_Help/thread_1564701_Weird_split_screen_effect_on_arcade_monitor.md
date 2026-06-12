---
title: "Weird split screen effect on arcade monitor"
date: 2010-08-30
forum: General Help
---

### Post by ArcadeNerd on 2010-08-30
I've been using Ubuntu for a while on my laptop so  I thought I'd also run it on my arcade machine. The monitor can handle a resolution up to at least 704x513 60hz (the resolution the original arcade game used) and uses composite sync. I've spent some time using xrandr to get the resolution, refresh rate and sync polarities that I need. 

These are the commands I used to set my resolution.

gtf 640 480 60
xrandr --newmode "640x480_60" 23.86  640 656 720 800  480 481 484 497  -HSync -Vsync
xrandr --addmode VGA-1 "640x480_60"
xrandr --output VGA-1 --mode 640x480_60

also tried 

gtf 640 480 60
xrandr --newmode "640x480_60" 23.86  640 656 720 800  480 481 484 497  **-Csync**
xrandr --addmode VGA-1 "640x480_60"
xrandr --output VGA-1 --mode 640x480_60

But it has the same effect since I have the hsync and vsync wired into a composite sync anyway.

What I get is this weird split screen effect that's in the picture. It looks like I'm missing something I just cant figure it out! Thanks in advance!

- Also I've seen some similar posts referring to computer monitors and they usually end with someone saying to edit the /etc/X11/xorg.conf file (which I don't have for some reason :confused:) or to update video drivers which doesn't help since I'm not exactly dealing with normal computer monitor resolutions here :P

---

### Post by ArcadeNerd on 2010-08-31
I'm running Ubuntu 10.04, and the graphics card is an Nvidia GeForce 7300 SE. I've tried to get this thing to work with and without the Nvidia drivers installed. Hope that extra info helps :)

---

### Post by ArcadeNerd on 2010-08-31
Bump

Anyone even have a clue? Maybe you know what causes something similar to this in a normal monitor? Is there a problem with my modeline??

---

### Post by ArcadeNerd on 2010-09-03
Well I got this to partially work. I changed the modeline to the one below. You'll notice its an interlaced mode with a lower pclock. However it appears that Ubuntu + Nvidia graphics card do not display @ 640x480i 15khz hsync 60hz vertrefresh. I just got a 4" line of some of the screen though it was very clear. 

Modeline "640x480@65i"      12.32   640  672  712  744    480  491   494  505 interlace

I'm just posting so that hopefully I can save someone some effort. I decided to switch my Arcade compy over to Puppy Linux - which does support the weird resolution and allows you to tweak xorg.conf during the install process. Thanks anyway. ):P

---


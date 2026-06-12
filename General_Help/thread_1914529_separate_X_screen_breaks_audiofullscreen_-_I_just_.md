---
title: "separate X screen breaks audio/fullscreen - I just want to play N64 games on my TV!"
date: 2012-01-24
forum: General Help
---

### Post by BLuFeNiX on 2012-01-24
Hi,

My goal is to play mupen64plus on my TV. I tried setting up a separate X screen with my TV, but some things aren't working correctly.

1) I have no sound. The sound indicator applet shows no volume, as though I killed pulseaudio. 

2) I have no Compiz effects on the second display (my TV). At first I had no title-bars, so I tried running "export DISPLAY=:0.1 && compiz --replace". This restored the title bars, but I have no compiz effects. (wobbly windows, etc)

3) I can't launch mupen64plus anymore. When I use only my monitor (TV disabled), I can launch and play mupen in fullscreen with no problem. When I try to use my TV as a "separate X screen" mupen won't display any video (it won't even expand the window to fullscreen -- it just hangs and shows all black).

A few details that I hope will help:

* I use BOSE speakers via USB.
* The TV is connected to the same nVidia graphics card that my monitor is.
* The above problems go away when I disable the TV and restart X.

Also, I tried using "twinview" instead of "separate X screen", but when I launch mupen in fullscreen, half of it shows on each screen. It's not important that I have separate X screens, just that I can play in fullscreen on one display without affecting the other.

Thanks for your time reading this and trying to help.

---

### Post by BLuFeNiX on 2012-01-29
Bump. I'm open to suggestions of how to remedy this. I currently just change my xorg configuration every time (to be either my TV or my monitor) and swap it back. Is there an easier way? There must be some X guru out there.

---


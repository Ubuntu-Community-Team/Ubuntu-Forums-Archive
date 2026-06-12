---
title: "Video Stutter...."
date: 2006-03-26
forum: General Help
---

### Post by MrChips on 2006-03-26
I am having a problem with X stuttering.  Every second any video app (games, screensaver, DVD, etc.) will freeze or stutter.  What may be causing this is that the CPU seems to be ramping in cycles of 1 sec up to 30% usage.

I don't know what is going on, there doesn't seem to be anything running in the background.  Although this seems to have started ever since I got my internal Dialup modem configured.

Any help?  It's really annoying...

---

### Post by Hairy_Palms on 2006-03-26
have you enabled DMA? if not try 
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by MrChips on 2006-03-26
DMA helps out the DVD play but the problem I'm having may have more to do with OpenGL apps.  Like I said games and the screensavers seem to be taking a 1 second cycle skip.  And the CPU seems to be ramping up 30% at the same time.

Thanks for the heads up on DMA though.  I feel a bit blind in here sometimes.  Kinda like when you lose something and go digging everywhere for it but never find it.  But in the process you find a bunch of other stuff you had been looking for on another occasion that you had forgotten about altogether.  "Oh yeah, that thing...hmm I'll get started on that instead."

Anyways...why is the CPU ramping up?  Or is something else running?

---

### Post by nanotube on 2006-03-26
try running the system monitor (apps>system tools>system monitor) and see what's eating the cpu.
(or from command line, run "top"). that might help you figure it out.

---

### Post by terranz on 2006-03-26
I have DMA on but my DVD movies stutter.  The video stutters and the sound is perfect.

---

### Post by ladofnod on 2006-03-29
[QUOTE=terranz]I have DMA on but my DVD movies stutter.  The video stutters and the sound is perfect.[/QUOTE]

I have this problem as well. Here's the kicker tho:

a)sometimes this problem occurs for two or three days at a time, despite every attempt to stop it.

b)sometimes while this problem is occuring I can get one out of twenty videos to play with no problem

c)once this problem is not occuring one out of twenty videos play with perfect audio and slow video that can't sync of because the video is playing at "half" speed.

*all the above affects every video player on my machine (vlc,xfmedia,gxine,xine,mplayer,totem)

---

### Post by MrChips on 2006-03-29
[QUOTE=nanotube]try running the system monitor (apps>system tools>system monitor) and see what's eating the cpu.
(or from command line, run "top"). that might help you figure it out.[/QUOTE]

The programs are random at most (metacity, gam_server, modem_applet, gnome-settings-dameon), cycles of about 5 secs, taking about 1% CPU.  Not much going on there.  This is a steady 1 sec stutter.  Mostly seen on the screensaver and games.

---

### Post by MrChips on 2006-04-20
Just to update this.  The problem was the modem_applet, the Modem Monitor added to the panel.  It was causing the stutter cycle.  I just removed it and everything is back to normal.

I have found this to be a problem in Breezy and Dapper (BETA).  The best thing to do for me is not use it.

---


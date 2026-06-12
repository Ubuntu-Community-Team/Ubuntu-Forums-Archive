---
title: "Strange audio problem"
date: 2010-07-17
forum: General Help
---

### Post by Kopachris on 2010-07-17
First off, running Ubuntu 10.04 64-bit with a Sound Blaster Audigy 2 card.  For some reason, the PCM channel in alsamixer is filled with a bunch of popping, while the Master channel is not.  However, Flash seems to send all its sound to that PCM channel in alsamixer, while all other apps (including Java, Rhythmbox, etc.) send their sound to Master, which doesn't have any popping.  (So I keep Master up by 100 and PCM down by 0.)  Other than telling OpenAL to use ALSA instead of Pulse (to fix a problem with the sound in X-Plane), I haven't really messed with sound much.  Pulse is still on my system, though I don't really mess with "Sound Preferences" or the volume applet, because they mess up what I have set up in alsamixer.  Anything I can do to get this somewhat more... streamlined?

---

### Post by Kopachris on 2010-07-20
Bump.  Also, Java from Firefox goes to PCM instead of Master, just like Flash.

---


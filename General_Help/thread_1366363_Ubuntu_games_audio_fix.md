---
title: "Ubuntu games audio fix"
date: 2009-12-28
forum: General Help
---

### Post by bruno9779 on 2009-12-28
I have been struggling with an amount of different solutions to have pulseaudio working in games like Regnum, HoN, Savage2, On the Rain slick precipice...

The sound would work for a while sometimes, but then always ended up crackling and finally muting.

With many games I have been unable to quit after the audio mutes, and I had to go tu a TTY session to kill pulseaudio.

But then I found [this]("http://www.regnumonline.com.ar/forum/showthread.php?t=51051") on Regnum forum:

> In the terminal:

sudo gedit /etc/openal/alsoft.conf

change the divice line form Alasa backend stuff to this:

## ALSA backend stuff
##
[alsa]

## device:
# Sets the device name for the default playback device.
device = alsa

Now all my games audio works fine!!!

I am not too sure what it does, so if anyone minds explaining it ....

---

### Post by Tamlynmac on 2009-12-28
I think this needs to be moved to the appropriate help section..

---


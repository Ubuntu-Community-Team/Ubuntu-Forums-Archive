---
title: "wine kills all sound from ubuntu"
date: 2010-10-15
forum: General Help
---

### Post by shanep-server on 2010-10-15
Has anyone got wine to funtion normally in Lucid 32bit...

If I launch anything

Pokerstars
Full Tilt
StarCraft II
Call of Duty 4

All my sound for Ubuntu is killed... if I close all wine programs sound resumes..Sometimes and other times requires a complete reboot.

I read that this is due to PulseAudio

I'm not sure of the difference between

Alsa
OSS
Jack
EsounD

Getting functional sound while running would be great...

I'm not a termial whiz or nothing but I get around... great at following directions LOL 

I installed wine from repositories an winecfg sound to ALSA

Even know just to make sure I had ALSA right ( while listening to rythembox ) Even going to winecfg > sound Killed my sound from rythembox.

---

### Post by ravi.xolve on 2010-10-16
Ubuntu uses PulseAudio. I have not tried sound with wine. Try this:

Upgrade wine.

Delete ~/.wine/ and run again.

---


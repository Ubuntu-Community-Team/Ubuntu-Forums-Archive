---
title: "Android emulator - no audio"
date: 2010-10-24
forum: General Help
---

### Post by mikelinux on 2010-10-24
Dear all,

this post may seem to be a bit off topic, but I am not sure it is something to do with the ubuntu audio system or just with the android emulator.

Problem: 
I cannot play audio in the android emulator 2.2.
I am using ubuntu 10.10.

I've tried to launch the emulator with the following audio options
(and I tried to use root privileges as well):
-audio oss  -> I get a warning for audio not supported, fair enough
-audio esd
-audio alsa

Nothing happens with the latest two: emulator starts and runs ok, but
no audio of any sort is played and even if I try the -verbose mode I
don't see any error in the shell.

Is this due to ubuntu 10.10 using pulseaudio?

Does anyone have any clue?

Thanks,
Mik

---


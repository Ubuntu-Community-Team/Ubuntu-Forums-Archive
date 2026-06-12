---
title: "Wine grabs sound device. Can't play other sounds."
date: 2012-07-28
forum: General Help
---

### Post by Splooshie123 on 2012-07-28
It seems that wine is grabbing my sound device. I cannot play other sounds like videos and music while wine is running.

If it matters any, the program I'm running in wine is VBALink (visualboy advance fork). When I disable sound in the emulator, then I can play video and music again.

If I am already playing audio when I start wine, the emulator will give an error. Something like "Cannot create DirectSound". And the its *wine* that has no sound.

I think I understand that Ubuntu handles requests to the sound card through PulseAudio?
Don't know whether this is relevant, but the wine configuration says its using winealsa.drv for sound.

Thanks.

---

### Post by brainwash on 2012-07-29
Switching to winepulse might solve your issue, but it could cause other problems like disoriented sound output.

[**winepulse in ubuntu wine ppa**]("http://ubuntuforums.org/showthread.php?t=1960599")

---

### Post by Splooshie123 on 2012-07-29
OK. For some reason, starting wine while audio is playing results in no sound in wine, but no error either.

The reason I wanted both to be able to play together is that VBALink runs too fast if I disable sound emulation, so I set it to mute (still emulates, but doesn't actually play it).
I wanted to listen to music while using VBALink, so I guess the problem has been circumvented.

Technically this isn't a solution, so I won't mark this solved.

---


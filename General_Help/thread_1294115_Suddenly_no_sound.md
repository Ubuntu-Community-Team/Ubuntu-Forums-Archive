---
title: "Suddenly no sound"
date: 2009-10-17
forum: General Help
---

### Post by ojve on 2009-10-17
Hi

All of a sudden all of my sound has disappeared in Jaunty. I now hear only a low scratching noise whenever any sound should be heard, both for audio files streaming media etc.

I have no idea what has happened, and no idea how to get it back! The only thing I can remember changing is upgrading libsndfile1, but that's only for sound files right?

Please help, this is very important to me since my girlfriend lives on another continent, and I need to be able to use skype!

//T

---

### Post by hkais on 2009-10-19
Hello all,

same issue here.
I have changed nothing except that I can remember the libsndfile1 was updated by jaunty-update.

Now my Lenovo T61 has no sound at all.

bye

---

### Post by mathewd on 2009-10-21
same thing has happened to me, jaunty 9.04 on Dell Mini 9. 
seems my sound has just utterly died... no internal speakers, nothing from headphone jack, nothing. The only change I can think of that happened around this time is the auto-update of libsnd that the above posters mentioned.

I tried uninstalling it, then using Synaptic Package Manager to Force Version the prior version and rebooted. Nothing. Even tried removing PulseAudio for good measure, but again Nothing. Im still utterly without sound and cant for the life of me figure out why. Im new to Linux/Ubuntu, but have managed (usually with the help of this forum) to work things out, but this one has me stumped. ANY HELP is appreciated! Thanks :-)

---

### Post by P4man on 2009-10-21
ive seen updates mute the PCM channel. Make sure its not muted. Have a look by starting

```
alsamixer
```

from a command prompt

---

### Post by mathewd on 2009-10-21
ah, how stupid of me! thanks p4man, you were absolutely right. 

my PCM channel wasn't visible in Volume Control, but a quick click of Volume Preferences and checking the checkbox it to make it visible let me unmute it. (hopefully this will solve it for the two folks above). thanks so much!

---


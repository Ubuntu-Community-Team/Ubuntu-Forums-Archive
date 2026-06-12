---
title: "flash audio is fuzzy / scratchy after hard reboot?"
date: 2009-10-10
forum: General Help
---

### Post by dix0r on 2009-10-10
hey all, 

i'm running 9.04 on a dell studio 1555. had a few sound issues initially upon installation but everything has been running great until i hard rebooted the laptop yesterday. 

upon restarting, all audio was fuzzy (couldn't distinguish any tones at all - just heard scratching noises while listening to mp3s, for example). 

in system > preferences > sound, 'sound events' and 'music and movies' were set to auto detect. when testing auto-detect, the sound was scratchy. tried the other options and got everything going again with HDA intel STAC92xxx Analog (OSS)

however, i still have scratchy audio in flash videos (running firefox). any tips?

many thanks!

---

### Post by dix0r on 2009-10-10
forgot to mention another symptom was that alsa hung up a few times upon shutdown. 

anyway, used alsa mixer GUI to turn PCM volume back up to 100. not sure how it got changed or what caused it to start acting up in the first place, but as far as i can tell this has solved everything.

no static / crackling noise in flash videos, and was able to set playback back to auto detect with no ill effects.

---


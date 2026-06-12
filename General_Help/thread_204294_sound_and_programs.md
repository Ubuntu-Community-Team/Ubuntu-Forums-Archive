---
title: "sound and programs"
date: 2006-06-26
forum: General Help
---

### Post by maka on 2006-06-26
is there anyway to make it so my sound card works at full duplex?

in windows, different programs can output sound at the same time, but now when for example, my browser has a quicktime movie loaded and i try to play music, it wont work until i close the browser... it's kind of annoying actually ](*,)

---

### Post by vigleik on 2006-06-26
In general this should work. Check that you are using alsa, not oss or something else for sound. Having said that, some programs, especially proprietary ones, don't play nice and insist on monopolizing the sound. You can try installing alsa-oss, that might help.

Vigleik

---


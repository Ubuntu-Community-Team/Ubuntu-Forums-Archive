---
title: "Command to Determine What is Using Sound Port?"
date: 2006-02-11
forum: General Help
---

### Post by happyponcho42 on 2006-02-11
I recall from a while ago, a command I used that determined what application was using the sound port.  I can't seem to remember any part of it, so can anyone enlighten me here?

Basically, I'm trying to figure out what application is currently using the sound port, so I can close it to allow another program to have sound.  I've tried many of the 'multiple-sound' tricks (alsa-oss, esd, etc.), but I'd like to be able to do it manually whenever I run into a problem.

Thanks

---

### Post by happyponcho42 on 2006-02-11
```
fuser -v /dev/dsp
```

---


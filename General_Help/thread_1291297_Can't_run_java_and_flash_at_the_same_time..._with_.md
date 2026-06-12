---
title: "Can't run java and flash at the same time... with sound"
date: 2009-10-14
forum: General Help
---

### Post by just4now on 2009-10-14
For some reason, whenever I try to run java and flash at the the same time, whichever one I opened first wil have sound and the other won't.

---

### Post by khelben1979 on 2009-10-14
It would help to know some technical information such as:

1. What version of [Adobe flash]("http://en.wikipedia.org/wiki/Adobe_flash") are you using?
2. What version of [java]("http://en.wikipedia.org/wiki/Java_(software)")?
3. What version of Ubuntu?
4. What sound system are you using? (I would guess [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture"))

and one last question:

5. Have you had this problem before?

---

### Post by just4now on 2009-10-16
> **khelben1979 said:**
> It would help to know some technical information such as:

1. What version of [Adobe flash]("http://en.wikipedia.org/wiki/Adobe_flash") are you using?
2. What version of [java]("http://en.wikipedia.org/wiki/Java_%28software%29")?
3. What version of Ubuntu?
4. What sound system are you using? (I would guess [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture"))

and one last question:

5. Have you had this problem before?
I am using adobe 6, java 1.6, Ubuntu 9.04, yes ALSA, and yes this has happened before.

I'm sorry for not including that in the first post :(

---

### Post by khelben1979 on 2009-10-16
Adobe6?? You should be using the latest version of the Adobe flash player version 10.

When it comes to ALSA: take a look at how it's configured. Maybe something is wrong?

---

### Post by 3rdalbum on 2009-10-16
If you're using ALSA, then try it with PulseAudio - this is one of the problems that Pulse was meant to solve.

---


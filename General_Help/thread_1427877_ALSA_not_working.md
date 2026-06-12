---
title: "ALSA not working"
date: 2010-03-12
forum: General Help
---

### Post by Mr Nemo on 2010-03-12
It seems any program that uses ALSA the sound wont work. Pulse seems to work fine. Is there any way to correct this?

---

### Post by mac666 on 2010-03-12
try an upgrade, restore, something.
More info is needed, did it work before, et c?

---

### Post by Mr Nemo on 2010-03-12
Truly I don't know if it was working before or not. I never really use alsa for anything. Pulse works fine, and I tried reinstalling alsa before, but that didnt remedy anything.

---

### Post by ajgreeny on 2010-03-12
Pulse is really just the sound manager that needs alsa beneath it for everything to produce sounds, so I suspect your comment that ALSA does not work is not quite correct.

Have you run alsamixer in terminal to check that there is nothing that is set too low or muted?  If not, do so.  Otherwise I think there must be a configuration within ALSA that is not set correctly in some way.

This is rather complicated, I know, but pulse will not produce any sound unless there is ALSA, OSS or FFADO with it, as I understand things.

To quote Linux Format LXF130 magazine, published in UK this month >  "There is a symbolic relationship between ALSA and pulse and the latter needs the former to survive.  Pulse configures itself as a virtual device connected to ALSA, like any other piece of hardware"

---


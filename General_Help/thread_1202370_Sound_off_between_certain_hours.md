---
title: "Sound off between certain hours"
date: 2009-07-02
forum: General Help
---

### Post by gjtoth on 2009-07-02
Anyone know a way to turn the sound off between certain hours (aside from the volume knob)?

---

### Post by CatKiller on 2009-07-02
Setting cron jobs for ```
amixer set 'Master' mute
``` and ```
amixer set 'Master' unmute
``` at the appropriate times might work.

---

### Post by gjtoth on 2009-07-29
> **CatKiller said:**
> Setting cron jobs for ```
amixer set 'Master' mute
``` and ```
amixer set 'Master' unmute
``` at the appropriate times might work.

Worked like a charm.  Thanks very much.  Sorry for the delay.

---

### Post by jtech55 on 2009-07-29
> **CatKiller said:**
> Setting cron jobs for ```
amixer set 'Master' mute
``` and ```
amixer set 'Master' unmute
``` at the appropriate times might work.

just what i was looking for too! Thanks

---


---
title: "No sound on Dell MIni 10"
date: 2010-03-03
forum: General Help
---

### Post by blur xc on 2010-03-03
It used to work, and now it don't.  I would assume that something went amiss after a recent update, but don't exactly now for how long the sound hasn't been working.

The sound isn't muted- afaict, but nothing comes out of the speakers.

Any suggestions?

Thanks,
BM

---

### Post by spiderbatdad on 2010-03-03
a little more info might help.
what output when you run command:
```
cat /proc/asound/cards
```

---

### Post by blur xc on 2010-03-03
> **spiderbatdad said:**
> a little more info might help.
what output when you run command:
```
cat /proc/asound/cards
```

Thanks- I didn't know what the command was to display my sound card info-

```
cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xd83a0000 irq 22
```

BM

---

### Post by spiderbatdad on 2010-03-03
Please install linux-backports-modules-alsa-karmic-generic.
Then run sudo apt-get update && sudo apt-get upgrade and reboot.

---

### Post by blur xc on 2010-03-06
> **spiderbatdad said:**
> Please install linux-backports-modules-alsa-karmic-generic.
Then run sudo apt-get update && sudo apt-get upgrade and reboot.

Hey!  Thanks!  It's working perfectly now...

BM

---


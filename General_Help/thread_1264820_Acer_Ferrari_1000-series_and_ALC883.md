---
title: "Acer Ferrari 1000-series and ALC883"
date: 2009-09-12
forum: General Help
---

### Post by orrie on 2009-09-12
A buddy of mine have an Ferrari 1000-series that have no sound in the front speaker.
Have actually now tried the [HDAIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) without any results..

```

stian@laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 2bfa
Codec: Realtek ALC883

```

/etc/modprobe.b/alsa-base:
```

...
options snd-hda-intel model=3stack-dig

```
Have been trying this and reboot without any results.

And this without results:

```

...
options snd-hda-intel model=acer

```

Tried to force restart of alsa without any results..


How to maybe fix this?

---


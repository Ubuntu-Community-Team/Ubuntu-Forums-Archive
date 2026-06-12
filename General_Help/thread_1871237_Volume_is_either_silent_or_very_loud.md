---
title: "Volume is either silent or very loud"
date: 2011-10-28
forum: General Help
---

### Post by BrokenKingpin on 2011-10-28
In Xubuntu 11.10 (and 11.04) I noticed that my sound is either silent or very loud. In the volume slider, up to 1/4 volume the sound is almost silent, and then after that it jumps to what seems like max volume. It is very annoying because I then have to use the physical dial on my speaks to change the volume, instead of being able to use the keyboard shortcuts.

Does anyone know how to fix this? I don't seem to get this on my laptop, only my desktop. I have an ASUS M3N78-VM mobo.

---

### Post by BrokenKingpin on 2011-10-29
bump.

---

### Post by Toz on 2011-10-29
Hello neighbour.

Have a look at this link for a potential solution: [http://askubuntu.com/questions/15069/how-do-i-change-the-way-ubuntu-adjusts-my-volume-mixer-levels]("http://askubuntu.com/questions/15069/how-do-i-change-the-way-ubuntu-adjusts-my-volume-mixer-levels").

---

### Post by BrokenKingpin on 2011-11-01
Thanks for the information Toz, that does appear to be the same issue I am having. I will try the workaround/fix tonight.

---

### Post by BrokenKingpin on 2011-11-01
TOZ, that link provided a partial solution that will works fine for now. Thanks!

I set the following in ~/.pulse/default.pa
```

load-module module-udev-detect ignore_dB=1
load-module module-alsa-sink control=PCM

```

So this made it so that the PCM channel is adjusted instead of the master, which works far better. This works when adjusting the slider on the panel, but if I use the keyboard shortcuts it still adjusts the master. I worked around this by adding the keyboard short cuts to Super+UP/DOWN:
```

amixer set PCM 10+
amixer set PCM 10-

```

I tried setting the keyboard shortcuts to the media volume buttons on my keyboard, but it didn't work. Oh well, this gets me close enough to what I need.

I think the root cause is that the sound card driver is not reporting to palseaudio correctly. I will look to open a bug for this.

---


---
title: "Gnome 3.5 and Removing Alsa"
date: 2012-08-17
forum: General Help
---

### Post by nankura on 2012-08-17
hey guys

two quick question's. i was wondering how id go about the following situation's

- Getting the latest version of gnome 3.5 through a ppa maybe thats out in the wild
- Removing Alsa and keeping pulseaudio without removing ubuntu-desktop

---

### Post by tartalo on 2012-08-17
> **nankura said:**
> Removing Alsa and keeping pulseaudio without removing ubuntu-desktop

Are you sure that what you want is that?
[https://upload.wikimedia.org/wikipedia/commons/0/00/Pulseaudio-diagram.svg](https://upload.wikimedia.org/wikipedia/commons/0/00/Pulseaudio-diagram.svg)

---

### Post by nankura on 2012-08-17
im 100% sure, i used to do it all the time with 10.04, but now im always been prompted when removing alsa core packages to remove the ubuntu-desktop

---

### Post by efflandt on 2012-08-17
What do you intend to use in place of alsa?

I always thought that pulse was a front end for alsa, but somehow they seem to rely on each other.  On a tablet PC, sound worked in Ubuntu, but not Lubuntu, which had alsa, but not pulse.  Sound did not work in Lubuntu (no PCM device in alsamixer) until I also installed pulseaudio and pavucontrol (then PCM device appeared in alsamixer and sound worked).

---


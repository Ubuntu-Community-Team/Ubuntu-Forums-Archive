---
title: "Can't find /dev/dsp"
date: 2012-09-17
forum: General Help
---

### Post by purplebamboo on 2012-09-17
I installed vmplayer for my ubuntu 12.04. However, it could not connect to the sound device with a hint "Failed to open the sound device /dev/dsp: No such file or directory
Failed to connect virtual device sound."

I've checked and found that /dev/dsp is not existed. But I can still play sound using Rhythmbox.  Is there anyone knows how to deal with this problem?

---

### Post by purplebamboo on 2012-09-18
Is anyone knows how to deal with this problem?

---

### Post by purplebamboo on 2012-09-19
:(

---

### Post by asyr on 2012-09-19
You can go on the Virtual machine Settings and to select Auto detect for the Sound Card.

---

### Post by purplebamboo on 2012-09-21
> **asyr said:**
> You can go on the Virtual machine Settings and to select Auto detect for the Sound Card.

It works now. I don't know why. But there's no /dev/dsp exist yet.

---


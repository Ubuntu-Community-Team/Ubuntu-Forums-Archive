---
title: "No Microphone"
date: 2010-08-23
forum: General Help
---

### Post by RedSingularity on 2010-08-23
I have spent hours trying to get my mic to work.  It works fine with pulseaudio but one i remove pulse the mic stops working.  I just want to be using pure ALSA for sound and mic without any pulseaudio.  Any ideas would be welcome. :)

---

### Post by RedSingularity on 2010-08-24
Got it.  Deleted an option line in /etc/modprobe.d/alsa-base.conf

Everything is good now.

---


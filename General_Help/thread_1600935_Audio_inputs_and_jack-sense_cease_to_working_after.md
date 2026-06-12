---
title: "Audio inputs and jack-sense cease to working after a while"
date: 2010-10-19
forum: General Help
---

### Post by argab on 2010-10-19
After I boot up, both audio inputs (I use the integrated mic on my notebook) and jack-sense (integrated speakers/headphones) work properly, as they should. But after some time (from few minutes up to several hours) both of them cease to work simultaneously. After that the mic input levels turning gray and speakers don't work at all (when headphones were connected at that moment) or speakers don't mute when I connect my headphones (if headphones were not connected then). After I reboot, everything is okay again for some time, but then it happens again.
Setting mixer levels manually with alsamixer doesn't help at all. I also tried different snd-hda-intel model settings in alsa.conf, but that just made things messed up, so I stayed with auto setting. This way everything (inputs/outputs/sense) works as should until it simply stops working.

It's maverick, ALC268, ATI Azalia (Intel HDA), alsa 1.0.23, but I had this problem with karmic and lucid as well when I tried them. Now I want to switch from Win7, but this is the only thing keeping me from it.

---

### Post by argab on 2010-10-22
Anyone any ideas what can cause this?

---


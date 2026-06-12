---
title: "Now the internal microphone doesn't work"
date: 2012-08-09
forum: General Help
---

### Post by rva1945 on 2012-08-09
Hi:

I fixed the problem of the sound not stopping coming out from the internal speakers when plugging the headsets by adding this to the alsa-base.conf file (my laptop is a Lenovo):

options snd-hda-intel model=thinkpad

Now it works, if I plug the headset the sound will not come out from the internal speakers...but it came at a cost: now the internal mike doesn't work, headsets plugged or not, only the headsets' mike works, if plugged.

So?

---


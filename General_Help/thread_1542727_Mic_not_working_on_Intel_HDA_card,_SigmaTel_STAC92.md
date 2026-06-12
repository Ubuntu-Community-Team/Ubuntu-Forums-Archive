---
title: "Mic not working on Intel HDA card, SigmaTel STAC9227 chipset, Ubuntu 10.04"
date: 2010-07-31
forum: General Help
---

### Post by ubu_lin on 2010-07-31
HI everybody, I recently installed ubuntu 10.04 lucid on my assembled PC, I m able to play sounds properly, but my Mic is not working. system Information: Intel motherboard chipset D946GZIS.. Audio: HDA Intel, SigmaTel STAC9227 chipset..  I had installed PulseAudio volume control, and tried all adjustments, but not worked... tried to edit alsa-base.conf using all different codes suggested on other threads, still did not work... any help plzz. Thank you

---

### Post by ubu_lin on 2010-07-31
I'm very happy because my microphone is working now.  edited alsa-base.conf and added this line "options snd-hda-intel model=3stack" at the end....  "sudo gedit /etc/modprobe.d/alsa-base.conf"

---


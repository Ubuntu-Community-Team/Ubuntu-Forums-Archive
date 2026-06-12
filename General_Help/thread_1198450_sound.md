---
title: "sound"
date: 2009-06-27
forum: General Help
---

### Post by Willy3 on 2009-06-27
No sound in this setup: ubuntu 9.04, Dell 1504 laptop, ATI Azalia sound card.

lspci results:
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


aplay -l results: 
no sound card found

sudo modprobe snd-hda-intel results:
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Invalid argument

Any suggestions on where to from here???

---


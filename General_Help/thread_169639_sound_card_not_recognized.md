---
title: "sound card not recognized"
date: 2006-05-03
forum: General Help
---

### Post by brewman99 on 2006-05-03
i am having to trouble getting sound to work on my breezy badger install.

aplay -l recognizes my sound chip (CPQb0ab ES-1869) but when i try to activate proper driver using "sudo modprobe snd_es18xx...", i get the following error:

FATAL: Error inserting snd_es18xx (/lib/modules/2.6.12-10-386/kernel/sound/isa/snd-es18xx.ko): No such device
FATAL: Error running install command for snd_es18xx

Any ideas?

---

### Post by multios on 2006-05-04
Just a idea, but if sudo modprobe snd_es18xx doesn't work, how about adding snd-es18xx to your /etc/modules file?  See if it will load that way after rebooting.

---


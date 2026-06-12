---
title: "Sound problems. Do I have sound or not?"
date: 2006-05-29
forum: General Help
---

### Post by canci on 2006-05-29
Hello !

After I install Ubuntu 5.10, I naturally have no sound cuz of having the Aztech Soundboard dunno which model. 
In MEPIS I always run alsaconf and it works.
Here I had to modprobe, which works when I load

modprobe snd-azt2320 port=0x220 irq=5 dma1=1

n it seems to work. I edited /etc/modules 
GDM plays the bongo sound, BUT
upon entering Gnome or KDE (i have both, cuz i added KDE and some proggies from Kubuntu) I can turn up volume via the mixer but nth happens in the players. I tried playing ogg files (i have vorbistools).
When rebooting, the kernel refers to the soundcard and says sth about
not being able to get resources (i really forgot what it actually said.)
and also not being able to load sth like MPUblabla (which I recon must be the MIDI device).

Any idea?

TNX

---


---
title: "prevent alsa from starting?"
date: 2006-04-29
forum: General Help
---

### Post by multios on 2006-04-29
Is there a way to stop alsa from starting?
I use oss for my sound chip (es1371 module) and it works great. However, I can't figure out how to stop alsa from loading/starting at bootup. 
I did it somehow on HH, but that system is long gone and now I am trying to get BB working with the chip. 
No, I don't want to work with alsa ;)    I have tried with BB, Slack, Kanotix, Mepis, Arch, and too many others. The es1371/oss works great. 
I would remove alsa if I could, but it is tied in too tightly with BB/Gnome. 
FWIW, I even renamed the snd-ens1371 module to something else, and it was still loaded after rebooting!  I have tried renaming all alsa directories to ALSA. 
I still can't get sound. 
With PCLinuxOS, I can choose which module to load. That is sweet :) 

Thanks.

---

### Post by 23meg on 2006-04-29
Try this:
```

sudo chmod -x /etc/init.d/alsa
```

---

### Post by multios on 2006-04-29
Nope :( 

ls -l /etc/init.d/als*
-rw-r--r--  1 root root 5420 2005-09-29 08:12 /etc/init.d/alsa

lsmod |grep 1371 
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer


Before rebooting this time, I did "sudo modprobe -r snd_ens1371""modprobe es1371". After that, I went to the module directory and changed the name of snd-ens1371.ko to something else. Then I rebooted. How did the snd_ens1371 module load? 

btw- before doing the modprobe es1371, I did another lsmod |grep 1371 to make sure the alsa module snd_ens1371 was definitely removed  ;)

---


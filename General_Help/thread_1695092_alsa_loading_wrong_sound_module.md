---
title: "alsa loading wrong sound module"
date: 2011-02-25
forum: General Help
---

### Post by swapnadip on 2011-02-25
My desktop board is Intel DG965RY with on board sound

My ubuntu 10.10 native install loads snd_hda_intel as alsa sound module and there's no sound from the front panel headphone.

The front panel headphone is working fine in Windows.

So I have also installed Ubuntu 10.10 on VitualBox in Windows.
Here I found that the alsa sound module loaded is snd_intel8x0 and the front panel headphone sound is working completely ok. 

So I feel that I need to change the alsa sound model of native install to snd_intel8x0 inorder to fix the front panel headphone issue.

please guide me how to change the sound module....

is there any way by which i can copy some config files for alsa sound from my VirtualBox installation and paste them to my native ubuntu installation inorder to fix the front panel headphone issue?

---

### Post by dino99 on 2011-02-25
with synaptic, install gnome-alsamixer. Then into Applications -> sound -> alsamixer, set your prefs: sound levels, mute/unmute as you need

---


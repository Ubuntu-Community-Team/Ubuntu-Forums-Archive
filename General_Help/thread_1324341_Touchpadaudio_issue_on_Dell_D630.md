---
title: "Touchpad/audio issue on Dell D630"
date: 2009-11-12
forum: General Help
---

### Post by gradinaruvasile on 2009-11-12
I installed Xubuntu 9.10 on a Dell D630. Everything seems to be ok (although i was preparing for something bad), even my battery life went up 30 minutes (from 2 in hours Jaunty/Gnome to 2.5). 

Anyways i just connected my headphones and chatted on Skype. But something weird happened: when there was no audio output i heard a wery faint click like sound, i think it relates to the audio power management. No problem with that.
 But when i use the touchpad, i hear a static like noise in the right headphone - all the time when i move my finger on the touchpad. It seems related to the signals emitted by the touchpad device internally and that somehow gets mixed in. And it happens only when the audio device "switches off". If some sound is played, even a sound using app is launched and inits the device i no longer hear it. Of course until the sound card goes to sleep again.
I cant hear it on the built in speakers, only in the right headphone channel.

Its not a big bug but it is annoying. It wasnt present on Jaunty (but there wasnt this powersaving feature implemented either).

Exactly that happens if i have my earphones cable being close (and parallel) to the mouse cable.

Anyone else experiencing this?

P.S. I have ALSA installed only (the default for Xubuntu). I dont know if this matters though.

---

### Post by Tweak42 on 2009-11-16
I have same Dell D630 system as you and contributing to bug report here.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457710](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457710)

---


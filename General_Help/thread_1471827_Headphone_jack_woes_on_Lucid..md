---
title: "Headphone jack woes on Lucid."
date: 2010-05-03
forum: General Help
---

### Post by Tralce on 2010-05-03
I had a script that I assembled for 9.10, initially for my macbook, though it ended up working on an HP ProBook and my Asus g50v, that rebuilt alsa to allow the software-controlled headphone jack to function:

```
sudo apt-get install build-essential linux-headers-`uname -r` module-assistant alsa-source
sudo dpkg-reconfigure alsa-source
sudo module-assistant a-i alsa-source
sudo alsa force-reload

```

This, of course, no longer works on Lucid. The first time I ran it, assuming alsa and such had remained relatively unchanged between releases, it broke alsa completely. I ran the last three lines separately again and alsa resumed working, but no headphone jack still. 

The issue is this: The software-controlled jack switches off the laptop's internal speakers upon the insertion of a 3.5mm cable, but no sound comes out of the headphones. Alsamixer registers the existence of the jack and allows me to mute/unmute it, but shows no volume slider. 

What do I do next?

---


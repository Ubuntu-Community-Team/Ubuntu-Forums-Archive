---
title: "alsa upgrade script no sound 10.10"
date: 2010-11-16
forum: General Help
---

### Post by kirkface8 on 2010-11-16
just used the alsa upgrade script in 10.10 under headers 2.6.35-22
and after a reboot i have no sound. no mixer detects any devices.

thanks

---

### Post by efflandt on 2010-11-16
What did you try to install and what were you trying to accomplish by replacing most recent alsa 1.0.23 release version that was already in 10.10.  Although, for HDMI audio for some devices you may have to do some configuration.

I created /etc/modprobe.d/sound.conf for snd-hda-intel options and created /etc/asound.conf configured so alsa would follow "Sound Preferences" (pulse audio settings) for analog or NVIDIA HDMI stereo.

---

### Post by kirkface8 on 2010-11-16
> **efflandt said:**
> What did you try to install and what were you trying to accomplish by replacing most recent alsa 1.0.23 release version that was already in 10.10.  Although, for HDMI audio for some devices you may have to do some configuration.

I created /etc/modprobe.d/sound.conf for snd-hda-intel options and created /etc/asound.conf configured so alsa would follow "Sound Preferences" (pulse audio settings) for analog or NVIDIA HDMI stereo.
yeah i realised the mistake after id done it.
i ran this script on 10.04 and it worked great.

i was getting some feedback on the speakers as well as no sound in tuxguitar
i though using this script could fix those problems.

should i remove everything and run this script again?

---

### Post by muzdaaz on 2010-12-12
I got the same problem, i know i did it wrong, but how the hell can i restore the original state of alsa???

---

### Post by Shellboy on 2011-01-12
Hi efflandt!

A friend of mine is getting started with ubuntu on his qosmio g50.
He doesnt have HDMI-audiosupport with his GeForce 9600M GT.
Is it possible to configure ALSA to support NVIDIA HDMI stereo with this card?

---


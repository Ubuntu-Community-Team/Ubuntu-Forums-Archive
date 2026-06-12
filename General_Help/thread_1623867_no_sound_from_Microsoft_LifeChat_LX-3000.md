---
title: "no sound from Microsoft LifeChat LX-3000"
date: 2010-11-17
forum: General Help
---

### Post by manubbo on 2010-11-17
Hi guys,

I noticed someone already posted this, but I'm not getting that headphones to work, neither if I disable internal audio by blacklisting the module. I'm using  Ubuntu 10.10. Actually headphones are recognized, but no way I can get a test sound going through them. In skype used to work, but after a reboot they're working no more.

Something else I can try?

---

### Post by FlameReaper on 2011-03-11
I just started giving this headphone a run on this laptop, am running it on Ubuntu 10.10 as well. However actually it doesn't matter... Since Ubuntu is using PulseAudio, you should be able to install the PulseAudio Device Chooser and manager (padevchooser and paman) and use them to redirect the audio to the headphones. Ubuntu does detect this headphone, so it shouldn't be much of a sweat once you install these two packages.

Once you got it installed, run PulseAudio Device Chooser, click on its panel icon and go to Default Sink. Your headphone should be listed there.

... I'm still figuring out how to make Skype detect its microphone, though.

---

### Post by marxmarv on 2011-04-06
> **manubbo said:**
> Hi guys,

I noticed someone already posted this, but I'm not getting that headphones to work, neither if I disable internal audio by blacklisting the module. I'm using  Ubuntu 10.10. Actually headphones are recognized, but no way I can get a test sound going through them. In skype used to work, but after a reboot they're working no more.

Something else I can try?

 ALSA seems to like to set default volumes on sound cards to zero, which in its defense is the least surprising value for volume, but also the least useful.  I had to find the card with ```
aplay -l
``` and then set the mixer levels to more audible values with ```
alsamixer -c *cardnum*
``` or equivalent.  A ```
sudo alsactl store
``` when finished should save the mixer settings for restore at next boot.  After that, it was a simple matter of going into the Sound preferences and the volume control and routing my sources as I like them.  If your ALSA mixer settings are correct, check here.
 I can't wait for USB HID report descriptor override to get into the kernel so I can use the call button on the pendant.

---


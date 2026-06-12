---
title: "No Sound Lucid Lynx"
date: 2010-10-07
forum: General Help
---

### Post by musendrophilus on 2010-10-07
I've been tinkering with Lucid Lynx since yesterday. Works great except the sound does not work. Time and time again I have checked to see that nothing is muted i.e. sound preferences and alsamixer.

My laptop has a realtek alc880 sound card. The sound actually works when I decided to downgrade to Jaunty Jackal and I haven't changed a darned thing. Yet when I come back to Lucid Lynx my computer remains stubbornly mute.

Best solution I thought I had found was this one:
[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

Despite the name it's geared for Lucid Lynx as well.

After updating and rebooting there still is no sound. Why does the sound work under Jaunty Jackal but not Lucid Lynx? Only thing I've found that's confounding is this:

aplay -l
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advice please! I don't know why my questions are being studiously ignored.

---

### Post by musendrophilus on 2010-10-08
Well I'm working blind, I tried adding options snd-hda-intel model=ref to /etc/modprobe.d/alsa-base.conf which did nothing. I am stumped.

---

### Post by musendrophilus on 2010-10-08
And I made sure my group/profile is able to use audio. Still muted!

---

### Post by Merthod on 2010-10-08
It seems that your sound card should be supported.

In System->Preferences->Sound, in the Hardware tab, check all profiles there are available. One or more of then should work for you.

---

### Post by musendrophilus on 2010-10-08
The hardware tab is empty when I check that section.

---

### Post by 3Miro on 2010-10-08
Go to a terminal (Apps -> Access -> Terminal) and type:
```
alsamixer
```

This will let you set the volumes for all the channels. Make sure you don't have front or main or pcm muted. (use M to unmute)

If  this is the problem, you can add the corresponding sound channels to the mixer applet.

---

### Post by musendrophilus on 2010-10-08
> **3Miro said:**
> Go to a terminal (Apps -> Access -> Terminal) and type:
```
alsamixer
```
 
This will let you set the volumes for all the channels. Make sure you don't have front or main or pcm muted. (use M to unmute)
 
Already did that and mentioned it in OP.
 
> **musendrophilus said:**
> I've been tinkering with Lucid Lynx since yesterday. Works great except the sound does not work. Time and time again I have checked to see that nothing is muted i.e. sound preferences and alsamixer.
 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

---

### Post by 3Miro on 2010-10-08
My bad.

Do you have sound if you boot from the LiveCD. The question is if this an issue with the driver or a settings. If LiveCD doesn't work, then you have a settings issue. Otherwise it would be big.

---

### Post by musendrophilus on 2010-10-08
Actually I'm going to dual boot JJ, see what's there and compare with LL.
If all else fails then I'll wait for MM to come out on Sunday and cross my fingers that it's ready for prime time.
 
I try it just as a live CD when I get home tonight to see if the sound does work.

---


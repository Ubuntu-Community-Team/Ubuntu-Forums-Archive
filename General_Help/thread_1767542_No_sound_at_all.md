---
title: "No sound at all"
date: 2011-05-25
forum: General Help
---

### Post by DaveyCakes87 on 2011-05-25
Hey, I just installed Ubuntu 10.04. (Long Term Support version) and after installing, everything works fine, except for the sound. I don't hear any sound when I boot it up, when things are alerting me, or when i try to play any music, or video. I'm really at a loss for how to fix this, but I would love to get this fix by tonight.

Thanks.

---

### Post by IWantFroyo on 2011-05-25
Has it worked before?

Is the blue sound cable plugged into the green port (versus the blue)?

If so, type this in your terminal.
```
alsamixer
```
After that, its relatively self-explanatory. Turn your master volume all the way up, headphone volume, etc.


PS- Don't you mean 10.04? 11.04 is just a regular release. 10.04 is the LTS.

---

### Post by DaveyCakes87 on 2011-05-25
> **IWantFroyo said:**
> Has it worked before?

Is the blue sound cable plugged into the green port (versus the blue)?

If so, type this in your terminal.
```
alsamixer
```After that, its relatively self-explanatory. Turn your master volume all the way up, headphone volume, etc.
Not sure I follow what you mean by the whole blue sound cable in the green port...

However, I turned up the max volume on everything, even on Rhythmbox Music player. I've even tried the alsamixer terminal process. Still, I get nothing.

---

### Post by mikewhatever on 2011-05-25
Should probably start by making sure all the cables are connected correctly, and that the sound is not muted (there is a Mute checkbox).
The next step would be to identify the sound card.
From a terminal window:
```
aplay -l
```

---

### Post by DaveyCakes87 on 2011-05-25
> **mikewhatever said:**
> Should probably start by making sure all the cables are connected correctly, and that the sound is not muted (there is a Mute checkbox).
The next step would be to identify the sound card.
From a terminal window:
```
aplay -l
```
I only have my charger hooked up and I'm running on a wireless router, which has everything plugged in. I'm sure. Nothing is muted. Everything is at 100%.

This is what the terminal told me:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by DaveyCakes87 on 2011-05-25
Does anyone have an answer, or solution to my problem? I could really use it.

---

### Post by mikewhatever on 2011-05-26
@DaveyCakes87
OK, check out the screenshot. See the two checkboxes with 'Mute' next to them? Make sure they are un-checked.
Are the speakers you use internal or external? If external, there is usually a wire with the green plug that connects the speakers to the sound card. Make sure it's connected to the correct socket.

---

### Post by DaveyCakes87 on 2011-05-26
Thanks, Mike.

In my Sound Preferences, both options are unchecked as far as the mute button goes. And my speakers are internal, I believe. So, what do I do then?

---


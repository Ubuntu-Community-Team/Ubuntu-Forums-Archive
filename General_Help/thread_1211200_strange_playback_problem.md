---
title: "strange playback problem"
date: 2009-07-12
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-07-12
I recently had to downgrade my system to a dell optiplex gx150 p3 1ghz 256 ram. It has an onboard sound card, not sure of the specs on it though. At first I had just swapped my hdd from my fried mobo to the dell, I had noticed the the playback of any/all media was playing like it was in ffw, not really fast, just enough to notice though. I ended up reinstalling everything (shot in the dark) But it's still doing the same thing. Any idea's on what could be causing this?

---

### Post by northern lights on 2009-07-12
Please post the output of ```
sudo lshw -C multimedia
```

Thank you.

---

### Post by Feelin_froggy8877 on 2009-07-12
Thanx for the reply :), here ya go...

*-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by northern lights on 2009-07-12
Your hardware looks fine. What does```
aplay -l
```report?

---

### Post by Feelin_froggy8877 on 2009-07-12
Here ya go. 


**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by northern lights on 2009-07-12
Crap. Have you checked *alsamixer* and made sure nothing is muted?

---

### Post by Feelin_froggy8877 on 2009-07-12
Well I just did, mic and pc speaker were muted, but made no difference when I unmuted. This is quite annoying. Not sure if this matters or not, but even the login sounds do the same.

---

### Post by northern lights on 2009-07-13
Since '*aplay -l*' shows a device and nothing's muted in the mixer, your issue can pretty much only be pulseaudio related.

Off hand I'm out of methods of diagnostics - here's a free bump, at least.

---

### Post by Feelin_froggy8877 on 2009-07-13
Thanx, appreciate the help.

---


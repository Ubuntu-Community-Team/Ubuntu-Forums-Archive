---
title: "Sound is not coming in my Desktop after installing ubuntu 10.10"
date: 2011-02-15
forum: General Help
---

### Post by ajay.eeralla on 2011-02-15
hi all,
I installed ubuntu 10.10 in my HP Desktop, But in sound preferences under output tab two options are showing .
namely,
1.analog headphones
2.analogoutput

 i selected analogoutput but sound is not coming .
please help me ..

---

### Post by ahsan101 on 2011-02-15
> **ajay.eeralla said:**
> hi all,
I installed ubuntu 10.10 in my HP Desktop, But in sound preferences under output tab two options are showing .
namely,
1.analog headphones
2.analogoutput

 i selected analogoutput but sound is not coming .
please help me ..
Is it a fresh install or upgrade and before this was everything working fine?

---

### Post by afrodeity on 2011-02-15
This is an old guide, but it works for me.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by ajay.eeralla on 2011-02-16
it is fresh installed one

---

### Post by ajay.eeralla on 2011-02-16
i have default sound card 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by afrodeity on 2011-02-16
*Your sound just might be muted. See alsamixer section*

type alsamixer into a console. The space bar + M mutes or unmutes the channels, try this before moving onto next step in faq

---


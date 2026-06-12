---
title: "Sound coming through Speakers and Headphones at same time."
date: 2010-08-12
forum: General Help
---

### Post by imfreak130 on 2010-08-12
I just started using Ubuntu as my primary OS today, and everything has been pretty much running smoothly.


But I am now having a problem with audio coming through the Headphones and Speakers at the same time. I have tried to fix it using other forums, but nothing seems to help.

I am running an HP laptop, AMD Processor, with Nvidia graphics.
Model is G60-119-OM


Output of 
> aplay -l


card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by imfreak130 on 2010-08-12
Bumping, kindof need help..

---

### Post by Wafaa on 2010-12-19
I'm having the same issue. It says solved. How did you solve this?

---

### Post by florinpnicola on 2010-12-20
I had several issues with different soundcards, all solved by simply UNINSTALLING ALSA, I just installed the 2 main packages, alsa base and alsa utils, I don't know if leaving the others is useful or not.
I solved the issue of sound being played at the same time from the speakers and headphones and another issue with a Creative External USB soundcard not being able to record sound with the microphone.
So, BINGO!
Remember to REBOOT the computer after uninstalling ALSA.
Oh, make sure you have PULSEAUDIO installed when you remove alsa, otherwise, install it.
Unless you need ALSA for something specific, there shouldn't be any problem.:D:D:D:D:D:D:D

---


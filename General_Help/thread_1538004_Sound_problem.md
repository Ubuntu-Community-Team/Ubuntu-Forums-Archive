---
title: "Sound problem"
date: 2010-07-24
forum: General Help
---

### Post by emily22 on 2010-07-24
Hey everyone. First I must say I'm fairly new to Ubuntu. My sound was working fine until 2 days ago, but now it just doesn't. I can't play any songs, but I can get the system beep and the "master sounds" (if you run alsamixer it's the first column that I'm talking about). It seems that my sound card is recognized. I followed quite a few instruction I found online, but nothing seems to work. A couple more details:

- If I go to System -> Preferences -> Sound, in the Input tab there is no device for my sound input.

- If I type "sudo aplay -l" in the terminal, I get the following:
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Pleeeeease help! I don't know what other info to give right now, but I could test more things if you tell me what. :D

---

### Post by emily22 on 2010-07-24
Never mind, problem SOLVED. I installed esound and removed pulseaudio, and now it works. Skype calls work fine as well. :)

---

### Post by emily22 on 2010-07-24
Actually, I'll take that back. It worked... temporarily! After restarting the computer it again stops working. I can't play any song, the only sounds I can make are the master and the system beep. If I reinstall ubuntu-desktop it reinstalls pulseaudio and I can play songs again. But then skype calls won't work, it seems there is a problem with pulseaudio and skype calls.

Help?...

---

### Post by lidex on 2010-07-24
Not my forte so have a look here:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)
[http://blogs.skype.com/linux/2009/09/some_explanations.html](http://blogs.skype.com/linux/2009/09/some_explanations.html)

---


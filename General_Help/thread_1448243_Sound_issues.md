---
title: "Sound issues"
date: 2010-04-06
forum: General Help
---

### Post by Eoghan1 on 2010-04-06
Hi guys, this is my first post. Just installed Ubuntu a few days ago and have most things working except the sound.

Here is the information I'm given when I type aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am getting no sound at all, with or without headphones. 

Thanks, I'm not sure what to do.

---

### Post by lidex on 2010-04-06
If this is karmic first go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and work through some possible bugs. In any case make sure pulseaudio is set up correctly here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---


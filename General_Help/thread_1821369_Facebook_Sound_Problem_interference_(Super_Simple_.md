---
title: "Facebook Sound Problem interference (Super Simple Fix)"
date: 2011-08-09
forum: General Help
---

### Post by youngbuild on 2011-08-09
So as I've been on Ubuntu the passed few days on my ASUS Laptop it came to my attention that their may be an issue with FaceBook sound Interfering with the built in sound card. I don't know if this is a Laptop issue or maybe even a problem with the default ASUS Sound Card, but this problem never seems to occur on my Desktop computer. Weird. 

So the problem is when I open up Facebook receive a message but have another piece of audio (Youtube, Mp3, etc...) it seems to screw up the entire sound-card.

So far the only fixes Ive discovered have been disabling Facebook sounds by click on the config box bottom right hand gear of chat, or rebooting. 

Please feel free to add any advice you may have on this issue.

---

### Post by howefield on 2011-08-15
Thread moved to "*General Help*"

---

### Post by WyleECoyote on 2011-08-15
rule of thumb for me is "anything to do with sound I check pulseaudio" here is a howto just to make sure you have the pulse sound server installed and running, the best thing I have found about pulse is you can have mutliple sound cards all playing different sounds at the same time which is where it will help you most of all

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I change the settings in "PulseAudio Device Chooser" so it automatically starts, when you run the applet you can choose where you want the sound to go and 2 sounds on top of each other will not crash anymore <-- also fixes the Skype sound crash issues

---


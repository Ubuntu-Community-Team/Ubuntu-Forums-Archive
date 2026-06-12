---
title: "No sound in ubuntu please help"
date: 2010-06-05
forum: General Help
---

### Post by ibe2fly4chu on 2010-06-05
hello all. I recently did a clean install of ubuntu 10.4 and finally got everything working. All of a sudden my sound stop working and i can seem to tell whats wrong. The strange thing is though when i first turn on the computer i can here the drums at the login screen but after logging in there is no sound anywhere. I checked all the sound preferences and everything looks alright, nothing was muted. I am pretty much stumped..can anyone help me ?
Thanks in advance.

---

### Post by dino99 on 2010-06-05
first check that your hardware is well identified: system pref sound

then install with synaptic: paprefs and gnome-alsamixer (set your prefs: apps sound gnome-alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Barafu Albino Cheetah on 2010-06-05
Use programm called pavucontrol to make sure your sound card doesn't get muted or anything besides system sound has some volume setting.

---

### Post by Barafu Albino Cheetah on 2010-06-05
Use programm called pavucontrol to make sure your sound card doesn't get muted or anything besides system sound has some volume setting.

---

### Post by ibe2fly4chu on 2010-06-05
I did followed that troubleshooting guide you provided. Everything seems to be in order. The card is being recognized, and matches the correct output given by the website. The preferences seem correct as well. Sound still isnt working though =/

---

### Post by ibe2fly4chu on 2010-06-05
come on...any more suggestions? literally sitting for days trying to get this work...kinda getting annoyed with this whole thing. Someone need to report this asap. Sound was working fine untill you run update. Distributions supposed to be better not take 4 steps backwards >.>

UPDATE: well sine its taking hrs upon hrs to get response, il just post what ever info i find myself, hopefully someone come along and help me out. 
When i run sudo aplay -l is  : **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ibe2fly4chu on 2010-06-05
hmm still no reply...lol guess am talking to myself...hello me ^^

---


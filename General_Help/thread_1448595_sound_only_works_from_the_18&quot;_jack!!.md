---
title: "sound only works from the 1/8&quot; jack!!"
date: 2010-04-06
forum: General Help
---

### Post by ninjaaron on 2010-04-06
I just installed Ubuntu on my Compaq Presario CQ61, and there is no sound coming from the speakers. When I plug in headphones or speakers, no problem, but nothing from the speakers. When I boot to Windows, no problem.

---

### Post by RedSingularity on 2010-04-06
Check your sound levels in alsamixer

In a terminal type 

alsamixer

and make sure all your levels are up.

---

### Post by ninjaaron on 2010-04-07
Hey, I did some more searching and found that this is a common problem with this computer. Here's the fix, if anyone else is interested:

> **Valpskott said:**
> I have a Compaq Presario CQ61-225EO and I had sound through headphone jack but not from speakers.
The following solution fixed my audio problem in both Jaunty and Karmic Koala.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
At the end of the file, add these lines
```
ptions snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```


---


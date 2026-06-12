---
title: "No sound in LXDE"
date: 2010-09-26
forum: General Help
---

### Post by chantaspell on 2010-09-26
Hi, I have just  installed Lubuntu and its greeat! very fast! but I am not getting any  sound. I have tried ubuntu and my sound worked but on lubuntu it doesnt.

I should explain that I have completely removed ubuntu and installed  lubuntu from scratch.

I have looked at alsamixer and nothing is muted.

sudo aplay -l shows my sound card... 

 	

 	thomas@NB200:~$ sudo aplay -l
[sudo] password for thomas: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 

Any ideas what to do? Is there any package i can bring from ubuntu that  will solve this?

Many Thanks!

---

### Post by searchfgold6789 on 2010-09-26
Try installing the same software you used for ubuntu onto lubuntu.
They do use different software, right?

---

### Post by chantaspell on 2010-09-26
> **searchfgold6789 said:**
> Try installing the same software you used for ubuntu onto lubuntu.
They do use different software, right?

I am new to this linux thing...any idea which software i would install?

---

### Post by 0N3 on 2010-09-26
try installing gnome-alsamixer

sudo apt-get install gnome-alsamixer

---


---
title: "No Sound - Help!"
date: 2010-08-19
forum: General Help
---

### Post by ep1centre on 2010-08-19
Hi, 

I've just done a fresh install of the latest stable ubuntu and i have no sound drivers installed, i have a Zotac ION N330 motherboard and i have the restricted Nvidia Drivers enabled, every instalation of ubuntu i've done in the past the audio drivers have always installed themselves so i have no idea where to start!

I have checked in the audio options and there's nothing listed under hardware that's how i reached the conclusion that the drivers are missing!

I have also checked to make sure that it isn't something silly like amp off or sound on mute or anything like that, can anyone please help me reinstall/install the correct audio drivers?

Thank you.

---

### Post by silbak04 on 2010-08-19
```
sudo aptitude install alsamixer
```^ if that still doesn't work, I'll think of another solution

---

### Post by silbak04 on 2010-08-19
also in case it is a driver problem...in a terminal, show me your output of ```
$ sudo lspci
```

---

### Post by ep1centre on 2010-08-24
After restarting the confuter a few times the sound was back and I've never had the problem since... If only I could understand why linux does this...


It seems to me like linux has kind of a "modular" structure, ie bits of it can go wrong and it'll carry on going apparently ok with exeption for certain parts/features unlike windows where it either works or doesn't there's ups and downs to both I guess... It just annoys me that something can cause me so much head ache and then all of a suthen start working for no apparent reason...


Oh well thank you very much and sorry to bother.

---


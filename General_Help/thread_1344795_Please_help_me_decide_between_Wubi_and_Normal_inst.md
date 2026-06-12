---
title: "Please help me decide between Wubi and Normal installation?"
date: 2009-12-03
forum: General Help
---

### Post by mahela007 on 2009-12-03
I'm trying to install ubuntu 9.10 on my laptop. At the moment, I can't decide on whether to use Wubi or do a normal installation (dual boot).
I'd really like to be able to put my laptop to sleep or hibernate. However, from what I've read, that doesn't seem to be possible in a Wubi installation.
However, the hibernate function doesn't seem to work properly with the live CD either. Will the hibernate feature work in a normal installation of ubuntu? 
My laptop is an IBM R51e thinkpad.

---

### Post by arubislander on 2009-12-03
Hi... the working of the hibernate function depends on the size of your swap partition. If your swap partition is too small (i.e. smaller  than the amount of physical memory on your machine) you won't be able to save the current state of the machine to disk. 

That's why you can't hibernate with a live cd, there is no swap space available.

---

### Post by doas777 on 2009-12-03
I'd advise going with a manual install. wubi seems to work fine (never tried it myself), but starts to cause problems later on, when people want to get rid of windows, or reinstall windows/ubuntu without affecting the other os. 

additionally there is the possibility for a wubi install to cause problems that the rest of us can't help with, since it isn't widely used by the folks that know the most answers.

just my two bits. generally speaking, if you can reinstall windows, without wiping out your data partitions, then you have all the skills you need to install ubuntu to hardware.

---

### Post by pricetech on 2009-12-03
I'd go dual boot.  However I have never used Wubi so I can't really give you an objective opinion.

---

### Post by mocoloco on 2009-12-03
Having used both I would say you're in a spot for dual-boot. Wubi is great for people who are still fairly unsure about keeping Ubuntu. If you think there's a good change you'll stick with it then dual-boot removes the dependence on the Windows filesystem, and saves you the trouble of having to convert a wubi install to a real install.
If you're thinking about needing it to hibernate then you're already planning to use it a lot so you're beyond the ideal usage of wubi.

---

### Post by mahela007 on 2009-12-05
Done.. I used the normal dual booting procedure. Didn't use Wubi. thanks for the help.

---


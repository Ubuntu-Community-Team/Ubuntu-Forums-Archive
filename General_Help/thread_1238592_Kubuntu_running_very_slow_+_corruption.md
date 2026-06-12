---
title: "Kubuntu running very slow + corruption"
date: 2009-08-12
forum: General Help
---

### Post by spoons on 2009-08-12
On my laptop, Kubuntu 9.04 runs extremely slowly. It boots fine but doing anything is hell as it is so painfully slow.
Moving the mouse is fine but if I click on the K menu, it takes a good second or two to pop up and takes aaaages to resize. Having more than one window open slows the computer down a lot. I also get some corruption on the screen in places like in between text boxes  etc.
Here's the system:

Dell Latitude D600
Pentium M 1.6ghz
512mb ram
40gb HDD (Ubuntu has 6.5gb)
Radeon 9000 mobility 32mb.

Thanks for any help.

---

### Post by starcraft.man on 2009-08-12
I just looked up that gfx card cuz I wans't familiar with it, [here]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Radeon_R200_.288xxx.2C_9xxx.29_series"). I can't say this with certainty, but I think the cards just underpowered for KDE. That's a really weak card by todays standards, it doesn't even have support for openGL 2.0. Did you have this trouble with the live CD as well? I would imagine so. To be sure, go to System  Settings (k menu favourite) > Desktop > General Tab of Desktop Effects > Disable all desktop effects and compositing. That card isn't capable enough for those. If your still having trouble then ya, I think it's the card.

You might be much better served by moving to GNOME with Ubuntu or XFCE on Xubuntu, not as fancy as KDE, more suited to older machines.

---


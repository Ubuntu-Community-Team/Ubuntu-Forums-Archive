---
title: "Serious problem with display corruption"
date: 2011-11-06
forum: General Help
---

### Post by vtrader on 2011-11-06
Laptop with nvidia graphics

Fresh install of ubuntu with kernel 3.0.0 as standard. For the first few days things were running smoothly, then all of a sudden the screen become randomly corrupted and locks the system completely. 
I've already blacklisted the nouveau module because of the well known conflict, but that makes no difference.
Now the display corruption if frequent, sometimes from a fresh boot all i have to do is move the mouse and that corrupts the screen.
Also launching firefox seems to cause the corruption as well.
I've also tried the mainline kernel, but same problems.

What are my options?

thanks.

---

### Post by searchfgold6789 on 2011-11-06
I'm assuming you actually installed the drivers (if you didn't, you can do that from "Additional Drivers".) If you did install them, please list your hardware specs.
P.S. Run updates, too. The kernel's at 3.0.12.

---

### Post by vtrader on 2011-11-06
CoreDuo T2350, 2gb ram, 500gb hdd, nvidia 8400mg

I forgot to mention i use to have opensuse, but that developed similar probs, that the reason for doing a fresh install of kubuntu.

I'm using the recommened drivers, I have also tried nvidia drivers in my previous opensuse install.

This seems to be a hardware issue I think, graphics maybe overheating?

---

### Post by searchfgold6789 on 2011-11-06
By all means; check your fans and heatsinks. Them nVidia's get really hot. 
Also try all the different drivers to see if they work, and if they don't try the ones directly from the [nVidia website]("http://www.nvidia.com/content/global/global.php"). I was astonished to find that the automatic drivers did not work for me and I had to go and download them from nVidia :(. Good luck,
 - search

---


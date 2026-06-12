---
title: "Flashing Screen Problem Please Help"
date: 2010-04-04
forum: General Help
---

### Post by cereal killer on 2010-04-04
Hello all.

I have an old machine running Ubuntu 9.10 and XP. It is a P4 and Nvidia FX5200 card. Yesterday all of a sudden the screen started flashing black, the same type as when you install new graphics drivers and the resolution is changing. Only here it keeps happening over and over, the mouse isn't usable fully, the icons and menus are distorted, and I basically can't do anything. 

I ended up reinstalling 9.10 and everything was working fine until I installed EnvyNG to get my nVidia drivers. It required a restart, and once I logged in the same thing started happening. So I said screw this, and installed 8.04. Yet even in 8.04, once I used EnvyNG to install the drivers, the same thing happened.

A few other details

- XP works fine, although one time a similar thing happened on XP (not as bad), and was fixed with a reboot.
- This PC runs through a KVM switch, but I connected it directly and the same thing happens.

I've found no help via Google. Sounds like a possible hardware problem, but it seems to work fine in XP and only acts up in Ubuntu once I install drivers.

---

### Post by NightwishFan on 2010-04-05
The answer might be not to use Envy to install the drivers. ;) I am unsure if there is a more correct way try via System -> Preferences -> Hardware Drivers?

---

### Post by xifer on 2010-04-05
Which nvidia drivers have you installed - you should see three sets in package manger you should be using v 173.14.25 probably. if you have v96 or 185 or 180 get rid.

---

### Post by cereal killer on 2010-04-05
Thank you for your responses.

> The answer might be not to use Envy to install the drivers.  I am unsure if there is a more correct way try via System -> Preferences -> Hardware Drivers? 

I have tried this yesterday and the result was the same.

> Which nvidia drivers have you installed - you should see three sets in package manger you should be using v 173.14.25 probably. if you have v96 or 185 or 180 get rid. 

I always used 173 through EnvyNG, as did the Hardware Driver install I tried. Furthermore, this problem didn't start after a fresh install, nor did I tinker with anything. If it started from something, it had to be a regular Ubuntu update.

Just to do a little update on the situation, I decided to give the 10.04 beta a try. Unlike 8.04 and 9.10 which gave me some bogus resolution before I installed the drivers, the default resolution was my native resolution. I went on the Nvidia site to grab the latest drivers and install them manually. When I tried to, it gave me this line, **"the distribution provided preinstall script failed,"** and asked me whether or not I would like to proceed. Since I already have my native res by default, I opted not to because that line does not sound promising.

But I would still like to have a grasp on what happened, because down the road with further releases, I might not be lucky enough to get my native res by default.

---

### Post by xifer on 2010-04-05
> **cereal killer said:**
> Thank you for your responses.


But I would still like to have a grasp on what happened, because down the road with further releases, I might not be lucky enough to get my native res by default.

dunno if it's any help but i've never had much luck with getting drivers from nvidia site.  the ones on the ubuntu repos work best for me.

Are you using an unusual monitor with your graphic card perhaps?  have had some probs with that where have had to set various params in /etc/X11/xorg.conf

---

### Post by cereal killer on 2010-04-05
> **xifer said:**
> dunno if it's any help but i've never had much luck with getting drivers from nvidia site.  the ones on the ubuntu repos work best for me.

Are you using an unusual monitor with your graphic card perhaps?  have had some probs with that where have had to set various params in /etc/X11/xorg.conf

The repository drivers are the ones that I confirmed have this effect.

As far as my monitor, it is just a standard Dell 19".

---

### Post by xifer on 2010-04-05
> **cereal killer said:**
> 

When I tried to, it gave me this line, **"the distribution provided preinstall script failed,"** and asked me whether or not I would like to proceed. 

If that is the last thing that happened - or even if not - I'd remove everything possible and start again clean.  Hope someone else has some better idea...

---

### Post by NightwishFan on 2010-04-05
Yes, run the uninstall in the script and also search for installed nvidia packages and "Completely Remove (Purge) them. Then try to reinstall them in Synaptic or by the Nvidia method. Do not purge a package if it remove a lot of things, but do so if it just tries to remove "ubuntu-desktop" thats fine it wont remove anything else. If the ubuntu-desktop is removed, just re-add install it again.

---


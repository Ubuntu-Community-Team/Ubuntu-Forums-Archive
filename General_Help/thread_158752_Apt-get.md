---
title: "Apt-get"
date: 2006-04-11
forum: General Help
---

### Post by DeadMazzay on 2006-04-11
Hello.

I've installed around 1 Gig of packages using "apt-get install ..." and Synaptic.

The question is - do they leave temporary deb files on hdd or not? Can I free-up some space after serious installs?

---

### Post by xXx 0wn3d xXx on 2006-04-11
[QUOTE=DeadMazzay]Hello.

I've installed around 1 Gig of packages using "apt-get install ..." and Synaptic.

The question is - do they leave temporary deb files on hdd or not? Can I free-up some space after serious installs?[/QUOTE]
Yes they leave the packages around. Open update manager and then go under settings and then click preferences and then set it to autoclean every 1-2 days.

Put the following in terminal. Copy and paste:

> sudo apt-get clean This may take a while if you have alot of packages installed.

to remove all temp packages ot

> sudo apt-get autoclean

to remove all old and unneeded packages. I would recommend useing the first one.

---

### Post by DeadMazzay on 2006-04-11
Oh, thanks a lot! It works :)

---


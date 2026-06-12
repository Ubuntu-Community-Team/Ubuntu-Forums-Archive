---
title: "Backtrack 5 freezes for no reason"
date: 2011-05-27
forum: General Help
---

### Post by kalera on 2011-05-27
Hi,I don't know if I am posting this on the right forum but I was hoping if anyone could help me solving my problem. I just downloaded Backtrack 5 and installed it. Had some problems getting the right driver for my gpu but eventually managed to install the right one. At first I thought the problem could be because I didn't have the right gpu driver but its still there. My backtrack freezes when I do anything,for instance I open firefox and browse the internet I can't open command promp or even close firefox with the close butten (alt-F4 does work). I can do 1 thing but then it just freezes and I can only do the thing I was doing. I can still browse but can't do anything else. I have the 64-bit gnome edition.
system specs are:
asus p6t deluxe V2
intel core I7 930 (2.80GHz)
nvidia geforce gtx 470
western digital caviar black 1TB

thanks in advance

---

### Post by wildmanne39 on 2011-05-27
> **kalera said:**
> Hi,I don't know if I am posting this on the right forum but I was hoping if anyone could help me solving my problem. I just downloaded Backtrack 5 and installed it. Had some problems getting the right driver for my gpu but eventually managed to install the right one. At first I thought the problem could be because I didn't have the right gpu driver but its still there. My backtrack freezes when I do anything,for instance I open firefox and browse the internet I can't open command promp or even close firefox with the close butten (alt-F4 does work). I can do 1 thing but then it just freezes and I can only do the thing I was doing. I can still browse but can't do anything else. I have the 64-bit gnome edition.
system specs are:
asus p6t deluxe V2
intel core I7 930 (2.80GHz)
nvidia geforce gtx 470
western digital caviar black 1TB

thanks in advance
Hi, what version of ubuntu are you using? where did you get the driver for video card from? Are you using effects or the cube?

---

### Post by kalera on 2011-05-28
> **wildmanne39 said:**
> Hi, what version of ubuntu are you using? where did you get the driver for video card from? Are you using effects or the cube?
Backtrack 5 is ubuntu 10.4 if I remenber correctly. I got the driver from the NVIDIA site itself? I ain't using the cube or effects yet its just the basic installation.

---

### Post by wildmanne39 on 2011-05-28
> **kalera said:**
> Backtrack 5 is ubuntu 10.4 if I remenber correctly. I got the driver from the NVIDIA site itself? I ain't using the cube or effects yet its just the basic installation.
Hi,look in the additional drivers and see if there is a driver for your card there and try it, you will need to completely remove the one you have now, use this command to get rid of the driver only if there is a driver in additional drivers for your card.
```
sudo apt-get --purge remove
```:p

---


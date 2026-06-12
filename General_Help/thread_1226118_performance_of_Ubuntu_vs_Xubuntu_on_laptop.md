---
title: "performance of Ubuntu vs Xubuntu on laptop"
date: 2009-07-29
forum: General Help
---

### Post by e24ohm on 2009-07-29
Folks:
I have an older Celeron laptop 1.8 Ghz, with 1 GB of RAM that i tried installing Ubuntu on; however, the performance was low. I figured i would give Xubuntu a chance, and installed the OS; however, the system ran better with Ubuntu installed. The system doesn't run great, and is dog slow with Ubuntu, but it feels faster the Xubuntu. Has anyone else experienced this issue?

I tried installing both OS with the automatic configuration, and I tried both installs with a 2 GB swap.

---

### Post by Mighty_Joe on 2009-07-29
> **e24ohm said:**
> Folks:
 i tried installing Ubuntu . . . performance was low. I figured i would give Xubuntu . . .however, the system ran better with Ubuntu installed.

Um, what?  It was slow with Ubuntu, but ran better with Ubuntu?
The primary difference between Ubuntu and Xubuntu are the window manager.  Ubuntu uses Gnome and Xubuntu uses XFCE.  Xubuntu will perform better than Ubuntu if your computer's graphics card is poor or don't have much memory (< 512Mb).  Your bottleneck is probably that Celeron processor.  Watch top or a system monitor to see what's going on with the system.  If the CPU pegs at 100% whenever you do something, try a lighter-weight Linux distro like Puppy.

---

### Post by pmlxuser on 2009-07-29
on the overral xubuntu should run faster on older machine because it is sort of light weight on resourse use. on thing to keep in mind is that the core system is still ubuntu but the window manager is xface. so the perfomance might be different but still you are running the same system.

How ever you have mentioned on the system specs except the graphics. this might play a lot in the system perfomance speciall when you don't have the right graphic driver.
so check whether the graphics driver has installed correctly and check the settings

I run ubuntu on a machine close to your specs and it runs very well.

---

### Post by e24ohm on 2009-07-29
> **pmlxuser said:**
> on the overral xubuntu should run faster on older machine because it is sort of light weight on resourse use. on thing to keep in mind is that the core system is still ubuntu but the window manager is xface. so the perfomance might be different but still you are running the same system.

How ever you have mentioned on the system specs except the graphics. this might play a lot in the system perfomance speciall when you don't have the right graphic driver.
so check whether the graphics driver has installed correctly and check the settings

I run ubuntu on a machine close to your specs and it runs very well.It was not even responding at times when Xubuntu was installed. Just creating another user, made the screen gray out a few times, and trying to configure a printer...well that forced me back to Ubuntu.

---

### Post by e24ohm on 2009-07-29
> **pmlxuser said:**
> on the overral xubuntu should run faster on older machine because it is sort of light weight on resourse use. on thing to keep in mind is that the core system is still ubuntu but the window manager is xface. so the perfomance might be different but still you are running the same system.

How ever you have mentioned on the system specs except the graphics. this might play a lot in the system perfomance speciall when you don't have the right graphic driver.
so check whether the graphics driver has installed correctly and check the settings

I run ubuntu on a machine close to your specs and it runs very well.I think the graphic's card is something 128 MB of RAM. the system is an old Dell 1150, from around 2000 - 2004.

---

### Post by pmlxuser on 2009-07-29
Have you tried to check on the forum Hardware I think there should be "Dell hardware " section you might be able to get more help there

try here

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

you can also ask there, guys there have dells

---

### Post by e24ohm on 2009-07-29
> **pmlxuser said:**
> Have you tried to check on the forum Hardware I think there should be "Dell hardware " section you might be able to get more help there

try here

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

you can also ask there, guys there have dellsOk thanks mate, will do...thanks for the help.

---

### Post by theozzlives on 2009-07-29
> **e24ohm said:**
> Folks:
I have an older Celeron laptop 1.8 Ghz, with 1 GB of RAM that i tried installing Ubuntu on; however, the performance was low. I figured i would give Xubuntu a chance, and installed the OS; however, the system ran better with Ubuntu installed. The system doesn't run great, and is dog slow with Ubuntu, but it feels faster the Xubuntu. Has anyone else experienced this issue?

I tried installing both OS with the automatic configuration, and I tried both installs with a 2 GB swap.

1.8 GHz??? I have a 1.73 GHz core duo and Ubuntu runs good on it (granted I have 4 GB RAM, but 1 should do fine). Must be the Celeron that's slowing it down.

---

### Post by e24ohm on 2009-08-03
> **theozzlives said:**
> 1.8 GHz??? I have a 1.73 GHz core duo and Ubuntu runs good on it (granted I have 4 GB RAM, but 1 should do fine). Must be the Celeron that's slowing it down.yeah, it is killing it, well I guess i have to wait for that new laptop until i stop spending money on my auto...and ccnp training material. thanks!!!

---

### Post by egalvan on 2009-08-03
What family of CPU that you have?

Pentium III

Pentium IV

Pentium IV Mobile?

If you still have XP install, then use cpu-id
this will give you all the info you need on the CPU
(family, stepping, socket, etc)

[http://www.cpuid.com/](http://www.cpuid.com/)

CPU-Z 1.52 is the latest as of today 03-Aug-09

For instance, I swapped out a P-III 1.8 Celeron for a P-III 1.6 with 1M cache...
 the increase in responsiveness was very noticeable.
The chip cost $12 shipped (eBay), well worth the cost!
(Dell laptop)

P-IV M running under 1.8 can usually be had for under $15 on eBay.

These are considered "ancient, obsolete" and the prices tend to agree.

Look for the highest-rated bus speed your machine can handle,
and look for more cache instead of higher core speed.

---


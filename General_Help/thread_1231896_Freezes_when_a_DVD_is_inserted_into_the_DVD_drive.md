---
title: "Freezes when a DVD is inserted into the DVD drive"
date: 2009-08-05
forum: General Help
---

### Post by MattTheRicker on 2009-08-05
Hi there,

I am running Ubuntu 9.04, Kernel Linux 2.6.28-13-generic, GNOME 2.26.1 with an ATI RV530 Radeon X1600 GPU. 

I just discovered tonight (having previously never needed to play a DVD under Ubuntu), that when I insert a DVD into my DVD drive, the system will freeze without warning, and I have to restart. 

Any thoughts? I am new to Linux, so if you ask me to try something, you will probably have to at least point me in the right direction in terms of how to go about it.

Thanks!

---

### Post by lisati on 2009-08-05
Does it freeze with just the one DVD or with all DVDs? Do the DVDs work in other machines?

There is some information on playing DVDs on Ubuntu here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by moster on 2009-08-05
Give us more info of your hardware.
```
sudo lshw
```
you can attach as txt or zip

---

### Post by MattTheRicker on 2009-08-05
lshw is attached. I had booted into Windows XP earlier to do some musical composition work in Finale (which sadly will not install in WINE), and the DVD played fine. I booted into Ubuntu, and without fail, I put the dvd in the drive, and 90 seconds later, the whole works freezes up. The first few times I tried to boot the system with the DVD in the drive, having forgotten it was there. It took me some time to realize that the DVD was the variable between the system running and freezing.

---

### Post by moster on 2009-08-06
I will tell you immeaditely that I do not know how to solve your problem.

I have very similar Asus MBO, and different problem but also with IDE devices. I cannot explain it or fix it, and it seems nobody else in here.

If I were you I would download latest Ubuntu alpha, load it from USB stick and see if I have that kind of problems there.

If you have SATA DVD-ROM instead PATA lying aroung you can try with it. I would do that in first place.

---


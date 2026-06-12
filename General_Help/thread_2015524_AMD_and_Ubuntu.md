---
title: "AMD and Ubuntu"
date: 2012-07-03
forum: General Help
---

### Post by t0p on 2012-07-03
I'm looking to buy myself a new laptop.  Most of the laptops I've been looking at use AMD processors - for example the  [**HP Pavilion g6-1325ea 15.6" Laptop - Red**]("http://www.currys.co.uk/gbuk/hp-pavilion-g6-1325ea-15-6-laptop-red-11884755-pdt.html"). It has a Dual-core AMD E2-3000M processor, and a AMD Radeon HD 6380G Discrete-Class graphics card.

I seem to remember that there used to be problems with Ubuntu and AMD chips.  Is this still the case?  Do I need to avoid AMD when choosing a laptop?  Or is everything better now?

Cheers.
[]("http://www.currys.co.uk/gbuk/hp-pavilion-g6-1325ea-15-6-laptop-red-11884755-pdt.html")[]("http://www.currys.co.uk/gbuk/hp-pavilion-g6-1325ea-15-6-laptop-red-11884755-pdt.html")

---

### Post by QIII on 2012-07-03
I've been using AMD for years with Ubuntu.

The issue right now, with the system you propose, is that many people seem to be having problems with the APU systems that also have descrete cards as well.

I tried to sneak off with my daughter's laptop while she was visiting this weekend, but she caught me before I could install a dual boot qnd experiment.

---

### Post by 3Miro on 2012-07-03
Older ATI video cards sometimes have horrible support on Linux. AMD CPUs and newer video cards work fine (AMD video cards do not play wine games well). Unless you want to run wine games, this laptop should work fine.

---

### Post by stderr on 2012-07-03
Slightly off topic, but it'it may be worth my clarifying this for anybody else who's uncertain.

AMD's *G terminology is used for on-core APU graphics. In my book, that counts as integrated graphics, not discrete graphics. This is because there is no separate graphics card. 

On [AMD's website]("http://www.amd.com/us/products/notebook/apu/mainstream/Pages/mainstream.aspx#2"), their blurb goes as such: "with the phenomenal *discrete-level* performance of AMD Radeon™ HD Graphics." (Emphasis added). I.e., they're claiming the performance is at the level of discrete cards, not that it is discrete. It's actually integrated APU graphics. 

As for its support; I'm afraid I don't know outright. I would expect it to be supported in their proprietary fglrx drivers, but how long that will run before they drop support is anybody's guess. The fallback is the open-source drivers, which are fine in a sense, but just rather non-performant in comparison.

As 3Miro intimated towards, how wise a move it is somewhat depends what you're planning to do with your laptop - gaming, per chance?

---

### Post by t0p on 2012-07-03
> **stderr said:**
> 
As 3Miro intimated towards, how wise a move it is somewhat depends what you're planning to do with your laptop - gaming, per chance?

I'm not much of a gamer - I play GNU Backgammon, and on occasion I'll have a bash at freedoom.  So I don't envisage much need for 3D acceleration or whatever.  I just want to know if the machine will work with Ubuntu for video and music playing, web browsing, wireless connection, messing around with python, uploading and downloading large files, photo management and image editing (Gimp)... pretty much a general-purpose work horse.

It seems you're all saying this laptop will meet these requirements; so I may well buy it.  Of course I'm going to have a bit more of a look round before parting with my pennies.  And if anyone here knows of a reason why the [**HP Pavilion g6-1325ea**]("http://www.currys.co.uk/gbuk/hp-pavilion-g6-1325ea-15-6-laptop-red-11884755-pdt.html") *isn't* a good choice for me, please let me know.  It's not very often I get the chance to buy a new computer, and I've been waiting to go 64-bit for absolute *ages* now.

Thanks for the feedback.

---

### Post by Linuxisfast on 2012-07-03
ASUS K53T with quad core AMD and dual ATI GPU works brilliant and stable with Ubuntu 12.04

---


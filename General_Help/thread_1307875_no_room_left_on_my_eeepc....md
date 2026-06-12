---
title: "no room left on my eeepc..."
date: 2009-10-31
forum: General Help
---

### Post by marie-p on 2009-10-31
I installed ubuntu netbook remix on my eeepc a few weeks ago and now I just realized that there was almost no room left on my computer. My eeepc has 20G of flash memory (no hard drive) and right now it tells me I have 512MB of available disk space. 
The only files I have are about a dozen pictures, one large mp3 file (about 70MB) and some documents. I added a few softwares, but I have removed all of them, except for one. I even removed all the games, and a few other softwares I don't need to get my space up to that 512MB. 

I don't understand how I can be out of room... does ubuntu really take up that much space??

---

### Post by joey-elijah on 2009-10-31
> **marie-p said:**
> I installed ubuntu netbook remix on my eeepc a few weeks ago and now I just realized that there was almost no room left on my computer. My eeepc has 20G of flash memory (no hard drive) and right now it tells me I have 512MB of available disk space. 
The only files I have are about a dozen pictures, one large mp3 file (about 70MB) and some documents. I added a few softwares, but I have removed all of them, except for one. I even removed all the games, and a few other softwares I don't need to get my space up to that 512MB. 

I don't understand how I can be out of room... does ubuntu really take up that much space??

Wow.

My eee-pc has 4GB and i have about 1.5GB of room left after installing NBR. (though i do remove a few applications i don't use.)

I'm not in Ubuntu atm but if the Disk Usage analyzer type application is still included by default it'll show you (graphically) where all your space is going.

Also worth running

sudo apt-get autoremove
sudo apt-get clean

to get rid of any cruft left by the applications you un-installed.

I can't imagine that Ubuntu hasn't eaten up 20GB for itself. You must have some large files knocking about you've fogotten of or perhaps you mis-partitioned the drive?

---

### Post by marie-p on 2009-10-31
Ok, I just figured it out... it didn't delete the files I had before installing ubuntu. Which is good because my backup malfunctioned. 

Now I have transfered the files I want into the right folders and deleted the rest. I just need to figure out how to re-partition the drives... there is now 13GB of space on the old partition (the one I don't use) and 373MB on the new one... 

Is there an easy way to fix this?

---


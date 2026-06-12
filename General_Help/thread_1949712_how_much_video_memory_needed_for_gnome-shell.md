---
title: "how much video memory needed for gnome-shell"
date: 2012-03-30
forum: General Help
---

### Post by alenn on 2012-03-30
How much video memory is needed for running Gnome Shell. I'm using Ubuntu 10.10 and when I install Gnome Shell it works so slow.
2.8 GHz Pentium 4
1 GB RAM
128 MB graphic card
.
.
.

---

### Post by 2048Megabytes on 2012-03-30
What are your other system specifications? What hard drive model are you using?  Have you tried Ubuntu version 10.04?

---

### Post by jerome1232 on 2012-03-30
> **alenn said:**
> 
1 GB RAM


Your system ram is pushing on the low side, is your system swapping a lot? Also what graphics card do you have, the video ram (especially if that's shared with the system, ie it's actually system ram being borrowed and used as video ram) isn't the only thing that matters.

---

### Post by alenn on 2012-03-31
I have GeForce FX 5500. RAM is DDR, and it's swapping around 500 MB. My system set swap on 500 MB so I assumed that it's ok.

---

### Post by mcduck on 2012-03-31
> **alenn said:**
> How much video memory is needed for running Gnome Shell. I'm using Ubuntu 10.10 and when I install Gnome Shell it works so slow.
2.8 GHz Pentium 4
1 GB RAM
128 MB graphic card
.
.
.

Don't worry about the amount of video RAM. If the graphics card is capable of running gnome-shell at all, it's going to be new enough to also have suitable amount of graphics memory.

In general, the amount of memory your graphics card has is pretty much the least significant thing to look at when thinking about graphics performance. (sadly, it also happens to be the one that gives nice big numbers for marketing purposes, which is the main reason why it's so often mentioned in computer specs... :/)

---

### Post by alenn on 2012-03-31
so, do you have a solution for this, can my PC support Gnome Shell or I have something else to fix

---

### Post by alenn on 2012-03-31
bump

---

### Post by jerome1232 on 2012-03-31
If you have the nvidia proprietary drivers installed and it's still slow, then you'll probably just need to try a more lightweight desktop environment, like xfce or lxde, maybe kde will run good for you.

---

### Post by alenn on 2012-04-01
yes, I've installed all Nvidia drivers. I've tried Unity, and it work like a charm, but Gnome Shell respond very slow

---


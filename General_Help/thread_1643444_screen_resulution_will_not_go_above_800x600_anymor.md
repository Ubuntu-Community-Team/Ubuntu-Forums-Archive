---
title: "screen resulution will not go above 800x600 anymore"
date: 2010-12-11
forum: General Help
---

### Post by sundays211 on 2010-12-11
I have copied this thread from the desctop environment forum as it has not received any responses there. I hope I can get more luck here in the general forum.

After the latest kernel update (2.6.32-26), my computer will no longer  start up with a screen resolution higher than 800x600. Before this  update, my computer would sometimes startup with this problem, but this  could usually be fixed with a restart (or two if necessary). At this  resolution the panels and a lot of tool-bars will not display properly,  so I am limited as to what I can do using the GUI. 

my video card is an S3 unichrome (I think. It is built-in to the motherboard so I don't know for certain)
my screen is an old ctr one
I am running Ubuntu 10.04 on the 2.6.32-26 kernel

any help would be appreciated

P.S. I have updated to Ubuntu 10.10 (fresh install) since writing this. The resolution still will not go above 800x600.

---

### Post by sundays211 on 2011-01-10
I have just noticed that some interfaces will not display fully in 800x600. Is there at least some way to get a virtual screen resolution (or possibly just a way to re-size the window so that I can click options that are hidden because they sit below the bottom of the screen)?

---

### Post by Bucky Ball on 2011-01-11
Go to Synpatics Package Manager and search for 'unichrome'.

You will find the open-source driver there. These VIA chips are not well supported in Linux (email VIA about that).

---

### Post by TechWiz2100 on 2011-01-11
Try installing drivers from Via or SourceForge

[http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action")

[http://sourceforge.net/projects/unichrome/]("http://sourceforge.net/projects/unichrome/")

---

### Post by Bucky Ball on 2011-01-11
I've been through the mill with Unichrome. There really is not much that can be done, VIA drivers, open-source, or otherwise. All pretty c****y. :(

---

### Post by sundays211 on 2011-01-11
Yeh. I have been actually trying to get an agp graphics card to replace it, because of all the trouble it has given me. But the only one i've found doesn't actually work so I'm sorta stuck with it. The odd thing with all of this is that I had been running it with the standard resolution of 1024x768 from Ubuntu 4.10 until 8.04 without any problems. It wasn't until I upgraded (and then fresh-installed) 10.04 that I stared getting problems where it would sometimes start up in 800x600 and wouldn't let me go any higher. Then after the kernel upgrade to 2.6.32-26 It refused entirely to go any higher. Even with several restarts (which used to work). I have since upgraded to 10.10 with the hope of fixing it. But no such luck. Anyways, you probably can't really help me (I am already running the openchrome driver by default, and I believe that I have tried others in the past (i'd raither try to avoid compiling from source if I can. They always refuse to compile without coming up with 50 errors requesting other packages). It would help enormously If you could tell me how to add a "virtual resolution" so that I can at least partially use, well, everything since almost nothing is designed to run on 800x600 anymore.

---

### Post by Bucky Ball on 2011-01-11
You should have kept 10.04 LTS (stable) and just booted into the previous kernel at boot if that was working. ;)

---


---
title: "Why are Nouveau drivers working better than NVIDIA's ?"
date: 2012-04-30
forum: General Help
---

### Post by kyfho23 on 2012-04-30
I was having an ongoing problem with my Ubuntu installation. This had persisted over several clean-install upgrades. At more or less random intervals, XServer would crash, and dump me at the login screen.

I finally had the idea to uninstall the Nvidia drivers, and try the Nouveau set. No crashes in 3 days.

I'm happy with things the way they are, except for loosing some of the eyecandy that seems to take 3-D drivers for.

Video card: GeForce 8600 GTS
Mobo: P5NSLI
OS: Precise, all updates applied
Nouveau Drivers info: Gallium 0.4 on NV84, 2.1 Mesa 8.1-devel (git-6af4c90 precise-oibaf-ppa)

As far as the Nvidia drivers, I had the same problem with the last 2 iterations of the current and current-updates available through Jockey. Haven't tried the 173 series.

Very odd.

---

### Post by kyfho23 on 2012-07-12
OK, I'm going to mark this "solved" because it sort of is. The problems with my video card stemmed from the rarest (to me) of all problems-actual hardware problems, to wit: A bad motherboard. 

Simple statistics convinces me that this is not the first time this has happened, but I've never heard of it before. Hard disk failures, yes, but never a problem with the non-moving problems.

So, if this comes up in results for a search you did, and you had other mysterious problems (mine included the odd problem that if I added RAM, networking would crash and the system would crash), you might want to think about the mobo.

The only unfortunate note in all this (aside from aggravation that stretched over several years), is that the board I replaced it with is older, and due to BIOS limitations, won't recognize all the RAM.

---


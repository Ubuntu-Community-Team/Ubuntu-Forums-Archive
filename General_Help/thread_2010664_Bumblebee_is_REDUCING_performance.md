---
title: "Bumblebee is REDUCING performance"
date: 2012-06-25
forum: General Help
---

### Post by Stonecold1995 on 2012-06-25
I just got Bumblebee working for my laptop (it's using nouveau drivers, the Nvidia ones seem to break X).  However, it seems to be reducing performance on some programs.  For example, using "google-earth" alone gives fairly good performance, but using "optirun google-earth" gives horrible performance!  It's especially pronounced when I try running games.  Specifically, Touhou Project.  Using just the CPU for graphics, my computer can run up to Touhou Project 10 without too much lag.  Any more and it's un-playable.  So I tried optirun on Touhou Project 08, and the FPS were reduced from 59 (just CPU) to 45 (with GPU?).  Why is this?  Why is the performance actually REDUCED?  Sometimes, it *does* result in a performance increase, like with Touhou Project 13 (2 FPS with CPU, 15 FPS with GPU).  I'm assuming it has something to do with those specific applications, because running "optirun glxspheres" gave about 75 FPS, but running "glxspheres" alone gave 1.5 FPS.

This is confusing because it's just Touhou Project.  It uses no complicated 3D graphics, and should run on most computers, so why is it *slower* WITH Bumblebee?  I tried experimenting with the different compression methods that optirun allows, but none of them gave any performance boost.

What am I doing wrong here?  Could it be because I'm using nouveau instead of proprietary Nvidia drivers (which for some reason don't work for me)?

---


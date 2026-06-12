---
title: "Unity doesn't start when I login"
date: 2011-04-29
forum: General Help
---

### Post by deadlock on 2011-04-29
Unity doesn't start when I log in with 'Ubuntu' set in GDM; instead it starts the normal Ubuntu Classic session. If I open a terminal and run 'unity --replace', Unity starts as normal (with full effects) but the gnome-panel is still running.

I'm not sure what's screwed up but does anyone have any idea how I can revert this so that Unity starts when I log in?

---

### Post by WING_43krat on 2011-04-29
I have the same problem and also does not move with the window open.

---

### Post by pd1108 on 2011-04-29
Same here.  when i installed 11.04 on my core-duo notebook (having 50 GB disk space ,6 GB ram and nvidia graphics - thru the upgrade route, towards the end it said my hardware does not support unity and it reverted to the classic screen (of 10.10).  that was rather unusual.  today I will try to install 11.04 using live CD and see what happens.  if that does not work either, then will revert to 10.10 and wait for a bug free version

---

### Post by pd1108 on 2011-04-29
Also by the way, I installed it (again thru the upgrade route) on two other computers.  in the first one - a core-duo processor desktop with ATI radeon card - after start-up the screen freezes and only a hard power-off solves the problem.  in short Ubuntu WILL NOT RUN

On the other computer - a notebook (again thru the upgrade route), the installation failed and will not load Ubuntu on start-up.  this notebook has Ubuntu installed thru the WUBI route.  interestingly on downloading the desktop version and creating a live-CD (actually live-USB), the installation went thru and it is working proper.

Wonder if there is a problem of the upgrade route. will be able to report after I tryout loading 11.04 on the other computers using live-CD/USB.

First impression of 11.04 - the Unity is just glitzy and it takes a while getting used to it. also it does not seem to be intelligent.  it is a chore moving from one open screen to another.  Maybe I dont know enough as yet, but it is certainly not intuitive.  I miss the simplicity of the 10.10 interface.

---

### Post by Yayestechlab on 2011-04-29
What graphics card do you have?

I had the same problem in a virtual machine and needed to enable 3d graphics acceleration.    

Here are the unity minimum requirements.
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---


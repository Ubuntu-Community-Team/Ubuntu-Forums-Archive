---
title: "Virtualbox VS Partition"
date: 2009-10-08
forum: General Help
---

### Post by chisle on 2009-10-08
what would you say are the upsides to running virtual box over partitioning your hard drive and running say windows? is it just better to dual boot or to just use virtualbox?

---

### Post by slakkie on 2009-10-08
Dual booting requires a user to choose: Do I run Ubuntu, or do I run Windows (or whatever distro)?

With a virtual machine you can still run the host OS (Ubuntu in my case) and run Windows at the same time. I don't need to shutdown my PC in order for me to run Windows when needed.

---

### Post by MelDJ on 2009-10-08
you can save space to. if you only need an OS for a specific use. for example, you want windows for internet explorer, its better to install it in virtualbox than using up a partiton. 
in addition you can choose how big the virtual  disk is. this saves money than buying a new disk when you disk is full

---

### Post by chisle on 2009-10-08
so is there any real downsides to using virtualbox - like will some programs not work on windows running in virtualbox?

---

### Post by kanikilu on 2009-10-08
> **chisle said:**
> so is there any real downsides to using virtualbox - like will some programs not work on windows running in virtualbox? VirtualBox is great (and I use it all the time), but games or other graphics intensive applications probably won't work, so that's a scenario where dual-booting would be necessary.

---

### Post by howefield on 2009-10-08
> **chisle said:**
> so is there any real downsides to using virtualbox - like will some programs not work on windows running in virtualbox?

Drivers are restricted to the virtual drivers supplied by Virtualbox, eg if you have a tv tuner that works in Windows,... it won't work in Virtualbox.

As previously mentioned, games may be a problem.

Hardware requirements are higher when running two or more operating systems simultaneously, eg, you need sufficient amounts of memory to share between them when they are running.

Nothing to stop you having both virtualised windows and dual booting, :)

---

### Post by CharlesA on 2009-10-08
The driver thing is a downside, but not by much. Example: I installed W7 in a virtualbox, but wasn't able to use Windows Aero (due to the video driver not being directx compatible.)

Not a big deal unless you want to run games inside of VB.

---

### Post by muteXe on 2009-10-08
Like people have said, what will you be using your windows to do?  If you wanna play gfx intensive games, make a partition. if you wanna code something up in visual studio, use VB :)

---


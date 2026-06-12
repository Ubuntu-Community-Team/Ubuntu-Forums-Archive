---
title: "Ocassional problem in graphics, Nvidia 8500gt"
date: 2009-10-20
forum: General Help
---

### Post by Loghtyrian on 2009-10-20
Hi

I've been using Ubuntu 9.04 for a few months now. But I've recently had some problems at startup, the graphics are 'slow' by this I mean that all the graphic effects I have enabled run at a low framerate, all the programs seem to run fine, this doesn't happens all the times (1 out of 5 times I start the PC) and I fix it just by restarting the computer. But still is annoying. Any suggestion?

My computer has a Nvidia Geforce 8500 gt graphic card and I have the latest drivers.

Thanks ! ! !

---

### Post by DeMus on 2009-10-21
> **Loghtyrian said:**
> Hi

I've been using Ubuntu 9.04 for a few months now. But I've recently had some problems at startup, the graphics are 'slow' by this I mean that all the graphic effects I have enabled run at a low framerate, all the programs seem to run fine, this doesn't happens all the times (1 out of 5 times I start the PC) and I fix it just by restarting the computer. But still is annoying. Any suggestion?

My computer has a Nvidia Geforce 8500 gt graphic card and I have the latest drivers.

Thanks ! ! !

When you say you have the latest drivers, which drivers are that? Installed from the nVidia site, or the ones from Synaptic?
Do you have 3D enabled, in other words does your cube spin? I ask this to find out if you have installed the drivers the right way?
If not, graphic performance is reduced because it is taken over by the CPU. Which would result in the low framerate you see.
I have played with Compiz for a short while but disabled it completely, it gave me more problems than I could handle. Also I don't like the effects. Now I have a stable system and that's what I like.

---

### Post by Loghtyrian on 2009-10-21
The drivers I refer to are the proprietary ones from Nvidia (version 180) and yes I have enabled the cube effect among others like the rain effect and other effects in windows. The strange part of this is that sometimes when I start the computer everything works fine (everything runs smoothly) and sometimes it doesn't (1 out of 5 times approx) :confused:

---

### Post by DeMus on 2009-10-21
> **Loghtyrian said:**
> The drivers I refer to are the proprietary ones from Nvidia (version 180) and yes I have enabled the cube effect among others like the rain effect and other effects in windows. The strange part of this is that sometimes when I start the computer everything works fine (everything runs smoothly) and sometimes it doesn't (1 out of 5 times approx) :confused:

Okay, so the drivers are okay. Just for testing, try switching of the effects. Right click the desktop, choose Change Desktop Background, TAB "Visual effects" and set the effects to none.
See what happens.

---

### Post by P4man on 2009-10-21
when its running slow, have a look in system monitor and see if any process is going berserk  Also check dmesg and /var/log/messages for clues. last thought.. if the videocard has a pci-e powerconnector, did you connect it to a power plug? Perhaps its not getting enough power over the PCI-E bus and reverting to some slow clock.

---


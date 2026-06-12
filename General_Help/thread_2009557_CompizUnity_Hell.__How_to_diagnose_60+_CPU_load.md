---
title: "Compiz/Unity Hell.  How to diagnose 60+ CPU load?"
date: 2012-06-24
forum: General Help
---

### Post by TrevorBradley on 2012-06-24
First some context:  I'm running Ubuntu 12.04 32 bit on a Quad Core AMD machine.  It's got a 6x2TB Software RAID.  I've been running Ubuntu on this machine since 10.10 beta, and have been an Ubuntu user since 8.04.  Everything had been running smooth and awesome until my 12.04 upgrade, and then things have gone to hell.

Soon after the upgrade, I started seeing massive CPU spikes, loads of 10, 30 - last night the CPU was up to 60.  The web interface locks up, though I can still move the mouse, or access a console if it is already open.  If I'm already logged into a terminal I can still access the machine, but a hard reset (and a consequential RAID rebuild) is the only way to get out of it.  I seem to have to reset every couple days.

To complicate the problem, I think 12.04 introduced RAID issues with my machine.  I think after a couple months of diagnosing this problem and I think I've gotten it under control.  I can verify the RAID continues to operate properly even under these conditions.  The system is now stable running Ubuntu 2D with the NVIDIA driver completely uninstalled (i.e. no compiz)

Mythbackend has also been problematic, but I don't believe this has been causing the freezing issues.

top indicates that compiz is the top CPU hog, though even after I got to init 2 there's some other process that's using up a large io wait portion of the CPU.  I kill off processes one by one, but after a while the whole system locks up and I have to do a hard reset.  iotop seems to indicate that no process is holding up the CPU, even though top says the system is spending 50% of its time in wait cycles.  There were 4 zombie processes the last time the CPU went up to 60, but the system locked up before I could diagnose which processess they were.

The log files show absolutely nothing wrong during these high CPU load times.  

I'm willing to plug away at various combinations to try to get this working.  My next course of action is to keep the NVIDIA driver installed but log in with Ubuntu 2D to try to figure out if NVIDIA is the source of the problem.   But I'm at my wits end on how to solve this.  Would upgrading the video card make the problem go away?  Have I not adequately isolated the RAID as a source of my problems?  What steps should I take to diagnose the system while it's in this high CPU state to determine what's wrong?

---

### Post by cyrus_the_virus on 2012-06-24
Hi,

I sometimes experience high CPU usage when the 'Sync to vblank" option is on. You could try setting it off.

First turn it off in compiz. Install ccsm, if you haven't already, and under "open GL" you can de-select the option.

Then switch it off in the nvidia driver: open the nvidia-settings program. You can find it under the "xserver xvideo settings" and open gl tab.

Hope that helps.

---

### Post by TrevorBradley on 2012-06-24
> **cyrus_the_virus said:**
> Hi,

I sometimes experience high CPU usage when the 'Sync to vblank" option is on. You could try setting it off.

First turn it off in compiz. Install ccsm, if you haven't already, and under "open GL" you can de-select the option.

Then switch it off in the nvidia driver: open the nvidia-settings program. You can find it under the "xserver xvideo settings" and open gl tab.

Hope that helps.

I happened upon a thread that suggested this... I set this in the NVIDIA settings but not in ccsm.  I'll leave Unity 3D on for a while and see how it behaves... if it can stay online for more than 2 days I'll be impressed, for 7 days I think there's a solution!

One important bit of info I think I left out is that one of the triggering events appears to be switching tabs in Firefox.  Not sure how relevant that is.

---


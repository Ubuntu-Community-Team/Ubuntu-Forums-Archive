---
title: "System Stutter running Heavy Load through Wine"
date: 2010-10-26
forum: General Help
---

### Post by klaxian on 2010-10-26
Hello folks.  I have recently begun contributing to the Folding@Home distributed computing project.  Due to oversights in the application's design and to process the most advantageous work units, I need to run this command line app through wine.  The application is very CPU/RAM intensive, but it does not put much load on the hard drive.  It is multi-threaded and uses up to 100% of all 6 cores in my machine.  I run it with a "nice" level of 19 with hopes that it won't slow down my normal desktop use.

Here is the problem... when running this setup, my system will frequently freeze for a fraction of a second and then resume.  With the more complicated work units, this can happen 1-2 times per minute.  During the freeze, the mouse will stop moving, videos stop playing, music pauses, etc.  The system is completely unresponsive.  However, each instance only lasts for a very short time.  Since this happens so often, my productivity is negatively impacted (and it's very annoying).

I previously ran the native Linux version of F@H without this problem, but that was also processing much less complicated calculations.  I have tried with wine 1.2.1 and 1.3.5 with the same results.  The application does not have problems running on Windows.  It has been suggested that the current Linux CPU scheduler is to blame, but is there anything I can do to resolve this now or work around it?  Any help is appreciated.

Here are my system specs:
Ubuntu 10.10 amd64
Tried with kernel 2.6.35 and 2.6.36 (ubuntu packages)
Tried wine 1.2.1 and 1.3.5
AMD Phenom II X6 @ 4GHz
4GB DDR3 RAM @ 1524MHz CL5
128GB SSD using the noop IO scheduler (trim enabled)

Thanks again!

---

### Post by lavinog on 2010-10-26
You mentioned that you are running it with nice.  Does the issue occur when you run it without nice?

It has been a while since I ran f@h, but didn't the windows version provide a graphical display?

Does wine output anything in the terminal when this happens?

---

### Post by klaxian on 2010-10-26
If I run it without nice then the process will have the same priority as my other applications.  I don't want anything to slow down because of F@H.  I want it to just use idle cycles.

I am using the command line Windows version, which is the only one capable of doing bigadv WUs right now.

wine doesn't output anything when the problem happens.  The wine devs said that wine shouldn't be able to cause this problem by itself since it runs 100% in the user space, which makes sense.  IMHO, nothing should have the ability to preempt all other system tasks including mouse movement.

---

### Post by lavinog on 2010-10-26
For debugging can you try running it without nice?

Also are you using any proprietary video drivers?  I have seen some drivers cause the entire system to freeze for a moment like you described.

---

### Post by klaxian on 2010-10-26
Running without nice has no effect.  The system is still completely responsive and usable actually, but the stuttering remains.

I am using fglrx 2:8.780 mainly so that I can use a dual-monitor setup.  I don't do any gaming on Linux (yet).  I can try manually installing Catalyst 10.10 if you think that would have any effect.  It's not just video that freezes though.  Audio and everything else is also affected.

Thanks.

---

### Post by lavinog on 2010-10-26
> **klaxian said:**
> Running without nice has no effect.  The system is still completely responsive and usable actually, but the stuttering remains.

I am using fglrx 2:8.780 mainly so that I can use a dual-monitor setup.  I don't do any gaming on Linux (yet).  I can try manually installing Catalyst 10.10 if you think that would have any effect.  It's not just video that freezes though.  Audio and everything else is also affected.

Thanks.

I don't know about the recent fglrx drivers but I had that issue with one of last years fglrx drivers.  Everything paused...it was like a system crash that recovers after a couple of seconds.
I should have a post about the issue somewhere on the forum.
what video card are you using?
I thought dual monitor support was available for the opensource radeon driver.  I haven't tested it out yet.

Edit: here is the post:
[http://ubuntuforums.org/showthread.php?t=1242819](http://ubuntuforums.org/showthread.php?t=1242819)

---

### Post by klaxian on 2010-10-26
I am using an ATI Radeon HD 5850.  I didn't suspect that this could be a video card drive problem, but I have had issues with ATI's drivers in the past.  I am currently downloading Catalyst (fglrx) 10.10 and I will give that a try.  The release notes say that support has been added for Ubuntu 10.10.  I'm not sure what that means exactly, but I will test it.

If that doesn't work, my next step will be to try the open source radeon driver.  Do you have any idea what the differences and limitations are?

Thanks.

---

### Post by lavinog on 2010-10-26
> **klaxian said:**
> 
If that doesn't work, my next step will be to try the open source radeon driver.  Do you have any idea what the differences and limitations are?

Thanks.

I haven't tried the radeon driver in maverick yet, but I have been using both lucid and the Xorg edgers version for a while, and I have been quite happy with it.
The Lucid version didn't have any powersaving features, but the newer version is supposed to be better at it, but isn't compatible with the lucid kernel.

I tried to install catalyst 10-9 on my lucid install, but it appears that there was a bug with dkms that prevented the modules from compiling correctly.

I have a RadeonHD3650 and a RadeonHD3200.  I don't do much gaming, but glxgears runs about as fast as fglrx did in 2008.  (glxgears is not that great of a benchmark of course.)

Here is the current feature list of the radeon driver:
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

### Post by klaxian on 2010-10-26
I tried the open source Radeon driver.  After much work and configuration, I learned that my card (cypress) is only barely supported.  There were errors/warnings in the log and the 2D and 3D rendering was hideously slow (600fps in glxgears vs. 2200fps with fglrx).  I thought I noticed some stuttering even with the radeon driver, but it's really hard to tell since everything was already slow and choppy.

I ended up running without DRI enabled for a while and I didn't notice any stuttering there, but I may not have used it for long enough.  The problem seems to vary.

Lastly, I did learn something interesting.  When running glxgears just now to compare framerates, the stuttering is VERY obvious and much worse.  I am getting ok framerates, but the gears stop and start.  They look choppy.  When the gears stop, so does my whole system including the mouse.  glxgears using the open source driver was smoother (though lower fps).

**Running glxgears with the fglrx driver WITHOUT F@H running through wine eliminates all stuttering and I get 5200fps.**

Does this point to a kernel scheduling problem?  I don't see how wine or F@H could cause this by itself since it runs completely in the user space.  Based on this additional information, what do you think the problem is?  Thanks again.

---

### Post by klaxian on 2010-10-26
I just proved that this is not a problem with wine or Folding@Home.  I was able to simulate "nice" CPU and memory load with a native stress test tool.  When running glxgears (nice level 0) at the same time, the stuttering is VERY obvious.  Every few seconds, the entire system freezes along with the gears for less than a second.

Does this mean that the problem has to be with fglrx?  Or is it just the sorry state of the Linux CPU scheduler?  Any other ideas?  How can I fix this?  Or is it just not possible to run any type of load while DRI is enabled?  Thanks.

---

### Post by lavinog on 2010-10-26
Based on my prior experience with fglrx, and the fact that it is closed source, and has had a history of regressions with the first two versions after an ubuntu release, my bet is on fglrx being the culprit.

Try running htop and see if you get that nan (not a number) error when the freeze happens.
I wonder if this is an identical issue.
I never responded to the forum post but the problem did go away when the next version was released.

---

### Post by klaxian on 2010-10-26
Good idea.  However I ruled out fglrx because I was able to reproduce the problem using the open source driver.  In addition, I was also able to see the problem running kernel 2.6.26 from a Debian 5 LiveCD so it doesn't seem to be Ubuntu's fault or a recent kernel change.

I am using the following command:
```
nice stress -c 6 -m 4
```

Once I execute that stress test, things start stuttering.  However, if I stress the CPU without involving much memory, there is no problem.  I am currently checking my memory for any possible hardware problems, but if that was the case one would expect Windows to display the same behavior and it doesn't.

I find it hard to believe that Linux is this poor at dealing with memory management and scheduling, but what else is there at this point?

---

### Post by klaxian on 2010-10-26
Ok it has to be something specific to this machine because I tried the exact procedure on a different computer without any problems.  So far all the hardware checks out.  Does the linux kernel perhaps not handle my specs very well?

AMD Phenom II X6 @ 4GHz
4GB OCZ Reaper DDR3 RAM @ 1524MHz CL5
Gigabyte GA-890FXA-UD5 motherboard
HIS Radeon HD 5850

(I have tried with stock and overclocked settings with the same result)

Any other ideas? :)

---

### Post by lavinog on 2010-10-27
What are the specs for the other machine that it didn't happen on?

---

### Post by klaxian on 2010-10-27
I tried the following and it didn't improve:
[LIST]
[*]Replaced power supply
[*]Replaced video card with an old nvidia 6200 PCI
[*]Tried both Gnome and KDE though the problem seems somehow less in Gnome.  Less effects maybe?
[*]Disabling all desktop effects (compiz)
[/LIST]

The specs of two other systems that don't have the problem are:
Lenovo T61 laptop
Intel Core 2 Duo T7300 @ 2.0GHz
2GB DDR2 RAM
nvidia Quadro NVS 140

AMD Athlon II X2 @ 2.9GHz
2GB (1x1) DDR3 @ 1333MHz CL9
Integrated ATI Radeon HD 4250
Corsair CX430 PSU
Gigabyte 880GA-UD3H motherboard


I'm running out of ideas.  Any other suggestions?

---

### Post by lavinog on 2010-10-27
When you checked the memory did you use memtest?

Also try using
```

tail -f /var/log/messages

```
And see if any messages pop up when it happens.

---

### Post by klaxian on 2010-10-27
memtest passed many runs and I even swapped out the RAM to be sure.  I have stress tested the system extensively to ensure stability.  Other than this stuttering problem in Linux under load, the system doesn't have any issues and has not crashed despite constant heavy load.

Nothing is recorded in logs or consoles when the problem occurs.

---

### Post by lavinog on 2010-10-27
Do you have a way to swap out the video card?

It could be a memory addressing issue with the video card memory.
There have been issues in the past with mtrr information being incorrect.

---

### Post by klaxian on 2010-10-27
> **lavinog said:**
> Do you have a way to swap out the video card?

It could be a memory addressing issue with the video card memory.
There have been issues in the past with mtrr information being incorrect.

See post #15.  I tried swapping out the video card already. The key data point here is that Windows works normally.  Doesn't that mean that it has to be something specific to the Linux kernel or Debian patches?  I plan to try Fedora, Gentoo, and possibly BSD to test that theory when I can.

Are there any other possibilities at this point?

---

### Post by meoconvn38 on 2010-10-27
It's better to run windows application using window:popcorn:

---

### Post by lavinog on 2010-10-27
> **klaxian said:**
> See post #15.  I tried swapping out the video card already. The key data point here is that Windows works normally.  Doesn't that mean that it has to be something specific to the Linux kernel or Debian patches?  I plan to try Fedora, Gentoo, and possibly BSD to test that theory when I can.

Are there any other possibilities at this point?

Sorry, forgot about that.

The only other thing I can think of is maybe check that you are using the latest bios.

Is it reproducible in a live cd environment?
I wonder if you can try the different versions of ubuntu, along with the other distros.

---

### Post by lavinog on 2010-10-27
> **meoconvn38 said:**
> It's better to run windows application using window:popcorn:

The issue is not with running the windows program anymore.

---

### Post by klaxian on 2010-10-27
**SOLVED**.  I hope this helps someone else avoid going through this process in the future.

Here's what I did:
[LIST]
[*] Compiled custom 2.6.35.7 kernel with -ck1 patchset including BFS scheduler to replace CFS.
[*] Configuration changes: enabled PREEMPT, upped polling from 100Hz to 1000Hz, disabled dynamic ticks
[/LIST]

Not only is the stuttering problem solved, but I feel like I have a completely different desktop.  Everything is much snappier - much quicker than Windows.  After setting the SCHED_IDLEPRIO flag on F@H, it is completely unnoticeable no matter what else I run.  This is how a desktop should be.  The only downside is that the system uses about 20% more power at idle (without CnQ + C1E).  However, since I fold 24/7, it's never idle anyway.

Thanks for your help guys.

---

### Post by lavinog on 2010-10-28
Awesome. Glad you found a solution.

You can mark the thread as solved using the thread tools menu at the top of the thread.

Question: Does f@h use all cores?

---

### Post by klaxian on 2010-10-28
Thanks.  I already marked it as solved :)

Yes, F@H uses all cores, but only idle cycles.

---


---
title: "browser performance slow?"
date: 2010-09-16
forum: General Help
---

### Post by reialist on 2010-09-16
Hello i have a Compaq Mini 311-1010sa yes its a netbook so optimal performance is a must I'm running 10.04, but basically what I wanted to ask is why is the windows version of chrome/firefox so much faster than the Linux version or is it just my netbook?

Within 10.04 moving ad's make scrolling un-smooth with no desktop effects & youtube video's break up (even low quality ones) but in Windows 7 I could watch a 720p youtube video's while using windows live messenger & being on face book without the slightest stutter.

this is the first time I've used Linux as a host OS  since 8.04 (Ubuntu has come so far since then)and I remember it was little bugs like this that made me go back to windows & I'm really considering going back to windows again.

Could installing 10.10 help?

P.S other native apps run fine.

---

### Post by harrismh777 on 2010-09-17
There are many factors involved when diagnosing performance degradation issues. There may be hardware constraints, memory constraints, resource locking/contention issues, and a host of other issues. 

More than likely your netbook (might also have been called a winbook) was specifically designed for, well, you know, that other OS.  :=}

The bottom line is that you are going to have to own the debugging. Open a terminal and run 'top' while you are running firefox.  See if you can figure out what's going on there. 

Performance issues are not necessarily bugs. As for going back to Windows, you probably left Windows for 'some' good reason.  It's still a good reason.

:)

---

### Post by lukeiamyourfather on 2010-09-17
Since that's an Ion platform, have you installed the proprietary nVidia drivers from the "hardware drivers" utility? No, installing 10.10 will probably not change anything without knowing the root of the problem.

---

### Post by Ahava591 on 2010-09-17
I have experienced this problem as well, OP. I'm running a respectable box, four gigs of DDR3, 7,200 RPM hard drive with a large cache, Phenom II X2 550 BE, etc.

I think it's just a problem with Firefox. I have seen this reported with Firefox and Ubuntu 10.04 at least one hundred times already, plus however many reports on the forums. Please be patient, keep your eyes and ears open for an update and don't let such a little thing send you back to Windows. You're stronger than that :)

---

### Post by AlanR8 on 2010-09-17
Would +1 the video driver install.

I've just done a full re-install of Lucid on my Sony VGN-FZ21S and the video performance was terrible.

Went into hardware drivers and installed the system "recommended" driver and all was well again.

Let us know...

---

### Post by reialist on 2010-09-17
> **lukeiamyourfather said:**
> Since that's an Ion platform, have you installed the proprietary nVidia drivers from the "hardware drivers" utility? No, installing 10.10 will probably not change anything without knowing the root of the problem.


yeah i have all the correct drivers installed

---

### Post by WorMzy on 2010-09-17
> **reialist said:**
> Within 10.04 moving ad's make scrolling un-smooth with no desktop effects & youtube video's break up (even low quality ones)

Could be a flash issue. Are you running 64-bit Ubuntu? Flash on 64-bit often causes problems as the plugin can use up CPU cycles for absolutely no reason at all.

There are ways around this. Check out a few other related topics on this forum, there's quite a lot of different ones, but none are guaranteed to work.

---


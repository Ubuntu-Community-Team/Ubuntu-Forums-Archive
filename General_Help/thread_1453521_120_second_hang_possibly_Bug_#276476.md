---
title: "120 second hang possibly Bug #276476"
date: 2010-04-13
forum: General Help
---

### Post by trouts2 on 2010-04-13
Ubuntu 9.10 hangs often when busy or idle. The monitor shows the desktop ok and the mouse moves but nothing will respond.  CTL ALT F2 sometimes responds mostly it will not.  A few times it has unfrozen but generally the plug needs to be pulled for a restart.  

  The Magic Sysrq commands show traces with the 120 hang notice and after googling around it seems like the traces and behavior match what has been posted in 276476 but I'm not sure. 

  The computer is a sock emachine D2823, Celeron D325 with 256MB 2.63GHz.  The memtest reports ok.  The system runs fine with XP.

  Ubuntu is very slow at giving focus to applications like the scheduler is thrashing and gets worse as apps are opened.  The hang will happen with just a terminal and browser going and the machine at idle.  Freezing up while idle for several minutes has happened several times.  
  It almost seems like the machine is going into semi or partial hibernation but leaving the monitor on and mouse on.  

  Is this bug 276476?  The system is Ubuntu 9.1 with all updates applied as of yesterday.

   Attached are a few lines from Sysrq.  I have logs with full traces, mem and blocked.

---

### Post by Objekt on 2010-04-13
I have seen that problem before.  Unfortunately, it seems to surface at random with Ubuntu 9.10.  I have seen it happen on one very old Dell (Dimension 4300 desktop), but not on another, almost as old Dell (Inspiron 8200 notebook).

I don't know that there's ever going to be a fix, since the problem simply doesn't occur with most hardware.  I haven't had one system freeze, in all the months I've run 9.10 on my hardware (listed in sig).

The only "solution" I've found is to use an older version of Ubuntu.  For example, a few months ago, I built a new system for the guy with the Dimension 4300 mentioned above.  I installed Ubuntu 8.04.3 LTS instead of Ubuntu 9.10.  He had tried 9.10 via Wubi install, and really liked it, but it kept locking up on him.  So, when I built his new system, I felt it was too risky to use 9.10.

That's not a great answer, but it's all I've found so far.

---

### Post by trouts2 on 2010-04-13
After more searching I think this is 539609 and not fixed.
My trace shows i915 as the process getting the 120 second timeout for being blocked.  The trace ends at __Mutex_lock_slowpath.

As mentioned in the initial post this can happen with the system unloaded and idle. I go to use the system and it's locked.  The mouse moves and the monitor seems alive but nothing gets focus or responds to a mouse click.

---

### Post by trouts2 on 2010-04-14
Objekt - I googled around and it seems you are right.  There are a few related bugs in i915 and some fixes but I still get the hangs. I've got a Dell 4400 and an Optplx270 so I'll either drop back to 8 or try 9.1 on the other boxes. 
Thanks for the help.

---

### Post by Objekt on 2010-04-14
No problem.  It's rather annoying that 9.10 introduced such a huge bug (among others).

I don't know whether the 9.10 freezeups are peculiar to older Intel chipsets or what.  The Dimension 4300 had an Intel 815 chipset.  The Inspiron 8200 had an Nvidia GeForce4 chipset, and did not experience freezeups.  Maybe there's a pattern.

---


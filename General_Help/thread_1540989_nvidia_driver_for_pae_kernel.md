---
title: "nvidia driver for pae kernel?"
date: 2010-07-28
forum: General Help
---

### Post by terry_opie on 2010-07-28
This is a followup/secondary question from another post earlier this morning.  ([http://ubuntuforums.org/showthread.php?p=9647704](http://ubuntuforums.org/showthread.php?p=9647704))

Info: Lucid 10.04, 4GB ram, Nvidia video, home built pc.

I'm fairly certain that when I enable the pae kernel this time, I'll get usage of the full 4GB of memory that I have installed.

The problem is, that I did enable the pae kernel earlier this week to test something out, but ran into a problem.  It came up in "low graphics mode" (800x600).  As you can image, I wasn't real thrilled about that.

I went to System->Administration->Hardware Drivers to get the video driver straightened out.  I figured it just needed one compiled for the pae kernel...  Well, it didn't find one.

Is there one?  Is there a procedure to get one installed/compiled, if there isn't one?

I don't know if I want to mess with trying to get the Nvidia drivers working for pae, when I only stand to gain another ~700MB of memory.  Currently showing 3.2GB.  I'm not sure if its worth my trouble...

---

### Post by terry_opie on 2010-07-30
Marked this as solved.  And for anyone else that may have this same issue...

After loading the pae kernel, the solution, rather than compiling a custom nvidia driver, was that once in the 'low graphics mode', to open up synaptic (or your favorite tool).  Remove the linux-headers-generic and add linux-headers-generic-pae...

I rebooted after that.  Video drivers were happy and my entire 4 GB of memory was available.

---

### Post by 1jackjack on 2011-09-13
worked for me, thanks terry_opie!

---


---
title: "Really Strange Startup Error! Space Invaders!?"
date: 2011-03-13
forum: General Help
---

### Post by dave2001 on 2011-03-13
I recently got a new HDD for my laptop. Did a fresh install of Ubuntu 10.04. The install worked fine, updated everything with update manager. 

The problem: Sometimes the startup process fails, but this only occurs randomly. When startup fails I am left with a black screen with a line of strange pixelated red characters along the very top of the screen (they actually remind me of that old space-invaders game). This occurs before the boot-splash or login screen can appear. The system in this condition will not respond even to a REISUB command. It has to be hard-booted.  Most of the time however, Ubuntu boots up fine with not a problem to be seen.

I also had this same error occur once when using the 10.04 live CD. (Please note: the cd is not the problem, I always check my md5 sums on downloads and verify burns).

Any ideas what could be going on here? I can post logs if someone can tell me which ones might be useful. Thanks in advance for any help.

If this helps.. I'm using a Thinkpad T60 with a Western Digital-250GB HDD.

---

### Post by dave2001 on 2011-03-21
So after some more digging, I think this is a graphics driver related problem. I have set "radeon.modeset=0" into my boot options, and have not had the problem since. 

Given that it was randomly occuring problem to start with, I won't be convinced that has fixed it for a while yet.

On a side note.. I'm not especially impressed with how the radeon driver is running my graphics card. The GPU temps tend be very hot. And the performance in certain areas leaves something to be desired. Given the lack of other options though, (since fglrx apparently isn't working anymore) looks like I'm stuck with it.

---

### Post by hictio on 2011-09-06
I have the same problem, but haven't found it on booting, at least yet. I cmae accross it while returning my T60 from Hibernate.

---

### Post by dave2001 on 2011-09-29
just wanted to confirm for anyone else with the problem.. changing the radeon setting at boot as described in my last post fixed the issue.

---


---
title: "Memory leak in console-kit-daemon, polkit and polkit-gnome-authentication-agent-1?"
date: 2010-01-28
forum: General Help
---

### Post by colinjones on 2010-01-28
I seem to be getting run away memory consumption with these 3 processes (at least). Ubuntu 9.10 (karmic), not running anything particularly taxing, with 2GB of RAM.

eg console-kit-daemon starts around 3.7MB after reboot, and over a couple of days cranks up to over 200MB! The other 2 are not far behind. These are physical memory values, NOT VM.

S.M., ps, and top all show much the same info. free -m slowly indicates that RAM (not including caches or buffers of course) is running out.

After a day or so, so much RAM is consumped that it starts paging to swap heavily and the swap used number starts going up and up (when it really shouldn't even be touched) and the box starts to slow to a grind, eventually it can take a minute to switch between apps because of all the swapping going on.

I have mitigated the performance issue, or at least delayed its onset to cranking down swappiness, and occasionally kill those processes... but clearly there is still an issue....

---

### Post by john_spiral on 2010-01-28
check your RAM from a live CD might be hardware?

---

### Post by colinjones on 2010-01-28
I don't believe so, this machine was running XP just fine for a couple of years, it has also run Ubuntu 0910 on a loopback for some time without issue, and I ran extensive RAM tests before installing... plus its only these processes, repeatably from reboot to reboot...

I have logged a bug upstream at freedesktop.org but it seems no one is interested... hoping I can get feedback from other users that may be experiencing the same thing...

Can you tell me what memory consumption you are seeing for these three processes, particularly after your machine has been running for several days?

---

### Post by MichaelHull on 2010-03-05
I'm having this problem too.  I am having this problem on 4 Ubuntu 9.10 machines.  I use the same applications on each machine.  Does anyone know what's causing this.  Eventually the RAM and Swap completely fills and the systems become unresponsive.  Does anyone have a solution at this time?

---

### Post by colinjones on 2010-03-17
Sorry mate, I still have this issue. I went to Freedesktop.org where these pieces of software came from and logged a bug report.

The guy responsible for this made a single, cryptic suggestion (aimed at a developer not a user) and then refused to comment again even though I posted repeatedly and practically begged.

A quick search of all other tickets allocated to the same guy shows that this is his normal mode of operation. Clearly he doesn't give a toss about the software he is looking after or its users. Is a real pity that the rest of the Freedesktop people haven't pulled him off that by now, as there are scores of open tickets, most of which have just been completely ignored....

---

### Post by vasiauvi on 2010-04-30
I have a similar problem just only that after 2 hours my memory is filled out![http://ubuntuforums.org/showthread.php?t=1466794](http://ubuntuforums.org/showthread.php?t=1466794)
It's because of the polkitd service and I also filled a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569711") and nothing!

It's crazy! At every upgrade on Ubuntu I have some kind of problems!

---


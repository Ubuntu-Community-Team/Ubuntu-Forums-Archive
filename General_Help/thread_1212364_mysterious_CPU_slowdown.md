---
title: "mysterious CPU slowdown"
date: 2009-07-13
forum: General Help
---

### Post by aregjan on 2009-07-13
I have a rather fast Dell laptop, with Core2 Duo 2.4GHz, 4GByes of memory.
I am running Ubuntu 8.04. Until very recently everything worked fine.

However, last week for a reason that I cannot identify it suddenly became VERY slow.
Quick benchmarks (through Hardinfo and other tools) tell me that my machine is now
WAY slower than the rest of the world.  Furthermore, I run a benchmark in matlab, and compared it with a previous one from a few months ago:  my laptop has become exactly 6 times slower! The slowness affects everything -- from simple computations, to graphics, to web browsing. 

First, I checked all the running processes in 'top' and 'ps'.  There was nothing suspicious.  Xorg would take ~5% of the CPU, and the rest of the processes were <1%.  The memory usage was also normal -- less that 20%.

So then I suspected that the problem could be with a recent upgrade of my VMware Workstations (I use it to run Windows XP).  First, I reverted to the older version.
That didn't help.  At that point I just stopped all the vmware daemons.  No change.

At this point I am out of ideas.  What else should one check?  Has anyone ever encountered anything like this?

---

### Post by eival on 2009-07-13
ive had this problem recently too, and i have a dual amd 2ghz processor an 2gigs ram

just browsing a few pictures will cause my laptop fan to start running an the processors usage keeps swaping from 100% on one, then the other one goes to 100% while the other one is around 20-30%

---

### Post by aregjan on 2009-07-13
Eival, when exactly did this happen? Last weel? If so, then maybe this is related to one of the daily ubuntu updates?

---

### Post by lovinglinux on 2009-07-13
It's probably the vino-server behaving badly. Go to "System >> Preferences >> Startup Applications (aka Session)" and diable "Remote Desktop" then reboot. This should fix the problem.

---

### Post by Finalfantasykid on 2009-07-14
do you have powernowd installed?  I tried installing it recently but it only led to problems.  After just a few minutes of using my computer the first time something even remotly cpu demading like watching a video in firefox, the fan would go on absolute maximum and the cpu would be downclocked to it's lowest setting, rendering my computer super noisy and unusably slow.

I uninstalled it, and things went better.

---

### Post by aregjan on 2009-07-14
lovinglinux, I went under System->Preferences->Session, however there was no mention of remote desktops.  On the other hand, by looking into dpkg --get-selections I see that vino is in fact installed.

---

### Post by aregjan on 2009-07-14
Ok, problem solved!

I did the following:

a) apt-get purge vino
b) apt-get autoremove
(removed nspluginwrapper, and some kernel headers)
c) fiddled with  cpufreq-selector -- only to be told that the
    service is not available.

The system performance is back to what it was.

---

### Post by aregjan on 2009-07-14
Ok, I went back and RE-installed vino.  The system performance remained high.
So it's probably not vino's doing.

At this point I am left to suspect (b)...

My thanks to everyone who gave advices and tried to help!

---

### Post by eival on 2009-07-15
> **aregjan said:**
> Eival, when exactly did this happen? Last weel? If so, then maybe this is related to one of the daily ubuntu updates?

yesterdays system updates for 8.04 required a system restart but i delayed it till i shutdown, so when i get home today an bootup ill see if perhaps the update fixed the issue.

---


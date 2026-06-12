---
title: "How to diagnose 11.10 Natty crash/reboots"
date: 2011-11-12
forum: General Help
---

### Post by DevynF on 2011-11-12
I'm quite new to linux, but not to computer troubleshooting.  I set up a new system with a fresh install of Ubuntu 11.10 (started with 11.04 and same problems) with the following specs:

[I]Zotac H55ITX-A-E MINI-ITX 
Intel Core i3 540 Dual Core Processor Clarkdale LGA1156 3.06GHZ Hyperthreading 4MB Cache H55 (integrated GPU) 
Crucial PC3-8500 4GB 2X2GB DDR3-1066
Western Digital Scorpio Blue 2.5IN 160GB[/I]

Install was smooth and the system seemed to work well.  Then it started crashing (is it called that in linux?) and the computer would reboot right to POST and back into Unity (is that right?).  It seemed the crashes were caused by video or audio playback at first.  Flash video seemed to be able to reliably trigger the reboot but not every time a video was played, likewise with audio playback in VLC.  Then we observed a reboot while word processing, and another while posting to a blog.  

Flash video is the most reliable way to cause the crash, but it seems to occur at random otherwise.  The system can be up for days without a hitch, then it will crash and reboot two or three times in a single evening.

1.  How do I pin down what's causing this?  Is there a log somewhere? Some monitor program I can run?
2.  I have this tingling sensation that it is video driver related.  Can anyone confirm?

---

### Post by dino99 on 2011-11-12
a few things to watch browsing folders with nautilus:

/var/log/
/var/crash/
/home/user/.xsession-errors

---

### Post by DevynF on 2011-11-12
/var/user/.xsession-errors was non-existent as far as I can tell.
/var/crash/ was empty
/var/log/ contains a lot of logs!  

I scanned through Sys.log and boot.log but nothing leapt out at me.  I'll keep careful track of the system time of the next incident and check all the logs again.

---


---
title: "New VGA cable doesn't Recognize Monitor, low resolutions"
date: 2011-01-24
forum: General Help
---

### Post by crfrop7311km` on 2011-01-24
Hello all, first time poster after having read gobs of threads trying to find the answer to my issue here.  

I'll try to post as much information as I can, and then will supply whatever else is inevitably left out and deemed necessary.

I'm running 10.10 on a Gateway MX3701 laptop which has an ATI Radeon Xpress 200M graphics controller (lspci | grep VGA) and am hooking it up to my Samsung P2770HD monitor/TV via VGA (VGA-0 port if that's important).  

So, the issue:  In resurrecting my old laptop by killing XP and putting on Ubuntu, I found I needed a VGA cable to connect to my monitor.  Borrowed a friend's to get my setup going, and all was well in 1920x1080 with all the other monitor settings working well too (laptop monitor off, etc...).

When my new VGA cable (cheap from Amazon) arrived and I shutdown, made new connection, and rebooted, my monitor was no longer recognized (it was before) and I am limited to weak sauce resolutions meant for my blinding grandmother.  

So I've tried to find similar issues on here and have struggled to do so.  I did find one thread that was similar, but the issue was never resolved.  

I am at your leisure to try any and all suggestions.  Thank you Ubuntu jedi.

crfrop

---

### Post by crfrop7311km` on 2011-01-27
bump

---

### Post by al2011 on 2011-05-17
Original VGA cable connects all it's 15 pins. 

Most none original VGA cable does not implement all 15 pins connection - use a multi meter tester to confirm. Older monitor / lower resolution is fine.. but hi resolution monitor requires the extra pins communication to the graphic adapter - without those pins, the graphic adapter cannot pick up it's native resolution.

---


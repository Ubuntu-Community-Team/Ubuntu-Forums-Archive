---
title: "Random kernel panics (Karmic)"
date: 2010-03-28
forum: General Help
---

### Post by MattP220 on 2010-03-28
A few weeks ago, I noticed that my system was hanging up over night. The screen would be entirely black and unresponsive, and the caps lock light would be blinking. I'd end up having to force a powerdown and restart. 

I did some checking and found out that this was a kernel panic. The log files weren't much help; nothing really stuck out to me as being an obvious cause or indicator of problems (but I'm far from an expert, so maybe I'm missing something). All they showed was that the error always seemed to happen somewhere around 730-830am, just based on system activity before the reboot.

At the time, I'd just done a kernel upgrade to 2.6.31-20-generic, so I tried rolling back a few steps. That seemed to help, as it wasn't dying on me every night, but then a few days later it happened again in the afternoon when I left it alone long enough to go inactive. 

Ever since, I can get maybe 36-48 hours of continuous up-time, and then I'll walk in and it'll be a B(lack)SOD. This is unusual as I've been using Ubuntu since 7.10 and I've never seen anything like this. Even Karmic has been working fine since November, until just a few weeks ago when this started.

Any ideas or suggestions? As it stands I can't even narrow down the cause, let alone try to fix it.

---

### Post by coolcaseley67 on 2010-03-28
Hi

- un-install your driver for you video and restart ,install any updates (2.6.31-20)with back ports & proposed ticked in software sources- update tab  . 


- then restart if needed and re-install your video .


hope it helps

---

### Post by MattP220 on 2010-03-28
Done. We'll see if that makes any changes.

---

### Post by coolcaseley67 on 2010-03-29
goodgood !!

---


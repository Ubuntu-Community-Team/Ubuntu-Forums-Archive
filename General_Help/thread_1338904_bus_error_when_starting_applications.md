---
title: "bus error when starting applications"
date: 2009-11-26
forum: General Help
---

### Post by hardbop200 on 2009-11-26
hello everyone,

on my desktop computer, I performed the latest 9.10 update as suggested by update manager.  since that time, it seems that I get one shot at starting applications, from that point forward, they will not start, and simply give me a "bus error".  

jackd:  I start jackd and it works perfectly, stop jack, then attempt to start again, it crashes.

firefox:  depending on the order I try this, I can start firefox, then every time thereafter, "bus error".

hydrogen:  again, "bus error".

I'm wondering if something in the upgrade has changed something on my system.  by the way, rebooting allows me to start these applications, then the whole thing starts again.

this problem seems kernel-independant.

any ideas?  I know I'm not giving near enough information to diagnose this, but /var/log/messages and /var/log/daemon.log doesn't seem to give any information.

---

### Post by GeordieDS on 2009-12-08
I've also been getting this behaviour on Ubuntu Studio. First with the RC install, then again with the full released installation. 

Not been able to find any information anywhere! Any help appreciated.

---

### Post by Sorseg on 2010-03-09
I have the exact same problem. Running Ubuntu studio 64x. Every application without instances running right now, crashes with "Bus error"

---

### Post by kewlbns69 on 2010-05-22
I'm having a similar problem. I upgraded to 10.4 running jack seems to be part of the problem. after jack's been loaded, all my programs give bus error and shut down. Does anyone know how to file a bug report? I have no clue how that system works but it seems like it might be a good idea.

---


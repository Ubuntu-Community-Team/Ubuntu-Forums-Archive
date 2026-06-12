---
title: "terminal: Spelling Errors!!!"
date: 2009-09-10
forum: General Help
---

### Post by kingtiger01 on 2009-09-10
Hello again everyone... i got a interesting little issue... 

im running Karmic Koala(server-2.6.30-x) and for some strange reason, all accross TTY1 i keep seeing random spelling mistakes.

while running Apt-get i see things like = 

$ apt-get install lynks
Readi.g package lists...
Bui8ding dependency tree
Reading state information... Done
...
unpabking replacement lynks
sett3ng up lynx...
...
~$
--------------

I cant explain it, its rather annoying, not so much a issue as a guessing game... it could be relative to my GPU(Gforce 7900GS, which has always run hot, almost to the point of not running) but, it runs within clock limits, so im not about to pull it for something stupid related to Framebuffer issues.

any ideas? ill report this to launchpad if its a unique issue.

---

### Post by egalvan on 2009-09-10
> **kingtiger01 said:**
> 
. it could be relative to my GPU(Gforce 7900GS, **which has always run hot, almost to the point of not running) **but, it runs within clock limits, so im not about to pull it for something stupid related to Framebuffer issues.



Just because it's "within clock limits" does not mean it's within heat limits.

Artifacts are one sure sign that the video is having "issues".

---

### Post by wojox on 2009-09-10
I'd mention it at launchpad or where ever. Alpha's are alpha's. Hurry up and work out the kinks would ya. :lolflag:

---

### Post by Whiffle on 2009-09-10
I doubt its a video card related issue.  Its switching out whole characters, not pixels.  

I would think it more likely that the character set is corrupt or something.

---

### Post by kingtiger01 on 2009-09-10
> **egalvan said:**
> Just because it's "within clock limits" does not mean it's within heat limits.

Artifacts are one sure sign that the video is having "issues".


Heat limits are clearly stated, by the clock-slow-down and outlined by NVIDIA, as 79*C, mine is currently running @ 56*C, its not beyond the heat-limits. and i have ALWAYS experienced Artifacts in text-consoles with this card, even in windows. until the driver was loaded(i used to use this card with my gaming machine, when it was new)
Given the fact 2 days ago, i pulled the card, removed the heatsink, cleaned and removed the old paste, put on some Articsilver, and she dropped 7*C. 


so i do-doubt its a issue related to the card-itself as i just experienced this same problem on my laptop, running Intel. which is running the generic-kernel, and nearly identical package installation(except of course server/workstation packages).

ill include screenshots if i can from ssh.

---


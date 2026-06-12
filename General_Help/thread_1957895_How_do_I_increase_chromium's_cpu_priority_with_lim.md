---
title: "How do I increase chromium's cpu priority with limits.conf?"
date: 2012-04-13
forum: General Help
---

### Post by x86scorpion on 2012-04-13
hi there!

I'm on ubuntu 11.10 and wanted to prioritize chromium browser's cpu usage on limits.conf, Is this correct?


   chromium-browser hard priority -10


How about item cpu?

 cpu
               maximum CPU time (minutes)

 priority
               the priority to run user process with (negative values boost process priority)


pls. need help..

---

### Post by raja.genupula on 2012-04-13
[http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/](http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/)

nice can help you .

---

### Post by idoitprone on 2012-04-13
> **raja.genupula said:**
> [http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/](http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/)

nice can help you .


.


x86scorpion: the cpu schduler is already the fastest it can be. Do you want to decrease latency? You can change your cpu scheduler
[http://kerneltrap.org/node/11778](http://kerneltrap.org/node/11778)

It the bfs scheduler, I have to abbreviate it because I donno the forum rules on profanity.

here is the ppa
[https://launchpad.net/~chogydan/+archive/ppa]("https://launchpad.net/%7Echogydan/+archive/ppa")

here is the website
 [http://ck-hack.blogspot.com/](http://ck-hack.blogspot.com/)

---

### Post by x86scorpion on 2012-04-14
Looks like the kerneltrap.org thing is beyond my knowledge, 
I'll stay with nice and renice for a while.


thanks for sharing your time! :KS

---


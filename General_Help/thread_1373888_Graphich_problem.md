---
title: "Graphich problem"
date: 2010-01-06
forum: General Help
---

### Post by crazyluca on 2010-01-06
Hi everyone,
I'm a new Ubuntu user and I hope to get an help with this problem. Firstly, excuse me if that section in not the right to pose my problem but I hope to find a little collaboration from you...so...I installed ubuntu 9.10. got no problem..works properly but sometimes, that mean that is not constant,I got black screen...like right now, I'm writing this post and I got a kind of flash black screen...this is really annoying me...I tried to check the visual effect but I didn't find any problem. The Compiz is not installed, got this card: 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
Express Memory Controller Hub (rev 03)

I really hope to find an help...thanks

---

### Post by duanedesign on 2010-01-06
Please attach your dmesg, /var/log/Xorg.0.log file from after reproducing this issue. An easy way to do that is wait until the screen flash occurs then run the following.

```
dmesg > dmesg.txt && cat /var/log/Xorg.0.log > xorg.txt
```

this will create two files in your home directory
~/dmesg.txt
~/xorg.txt
Attach those to a post on this thread. That will help in trying to track down your issue.

---


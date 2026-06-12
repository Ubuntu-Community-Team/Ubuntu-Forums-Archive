---
title: "Power and overheating/fan problems with ubuntu 11.10"
date: 2011-10-21
forum: General Help
---

### Post by Tremendouse on 2011-10-21
Hello all,

I have been experiencing weird problems after I installed ubuntu using wubi(however it is spelled). The first problem that was very very obvious is the power problem. With windows 7 I get about 4-5 hours of battery life. On ubuntu, I get around 1 to 1 hour and a half of battery life. The second problem I noticed is the fan, I have no clue why it is always on high, and sometimes it goes all out.

I have a windows 7, Alienware m15x. Specs:
i7-2820QM processor
Nvidia GeForce GT 555M
2nd Generation Core Processor Family Integrated Graphics C(integrated graphics card)

Also I want to mention that in windows I have an auto switching feature that switches between video cards. If i'm browsing or doing more like "light" activities, the integrated video card will be working, but if its heavy, the nvidia card kicks in.


I really love how fast and neat ubuntu is, but i really need to fix these problems or my laptop's life will be drained :P

---

### Post by Tremendouse on 2011-10-23
Can anyone please help?

---

### Post by aaadonai on 2011-10-23
Apparently is a Linux Kernel issue. Have a look on the link below for a possible workaround solution.

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by cozumel on 2011-10-23
I don't use wubi and am noob with Ubuntu too.  However, I think this is Optimus related problem with your 555M card.  If you disable the card in Ubuntu and use the intel graphics i7 then the battery usage will most likely cease.  Ubuntu is not able to switch between graphics cards.

Maybe that is not a factor with wubi though.

---


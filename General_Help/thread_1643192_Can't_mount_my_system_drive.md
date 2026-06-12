---
title: "Can't mount my system drive"
date: 2010-12-11
forum: General Help
---

### Post by m_zeid on 2010-12-11
Hello for all of you,

Well here is my situation, I had to install win xp and another ubuntu so I can try things with risk-free, after installing every thing, the new grub editor was installed, but not detecting y prvious ubuntu, and I tried updating grub 2 it also did't detect it.
so I went to Computer and tried to enter the system file drive but with no luck.
It tells me that it's unable to mount the drive.
I'm now on windows, I will be on ubuntu after few minutes and I'll post back exactly the error messege

---

### Post by sikander3786 on 2010-12-11
Hi.

So you mean that you've got more than one Ubuntu installs on your HDD and Grub is not picking all of them?

While in Ubuntu, I would suggest to run and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything we need to know about your setup and thus advise accordingly.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by m_zeid on 2010-12-17
Never mind. I solved it.

from the other ubuntu installation I used gparted to fix the correpted partition, and it did fix the journaling.

and updating grub and then>> VOILA I have my ubuntu back:p

---


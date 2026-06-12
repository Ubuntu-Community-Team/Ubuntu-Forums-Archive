---
title: "Bieeeegggeeeee bug!"
date: 2010-09-18
forum: General Help
---

### Post by crackbuntu on 2010-09-18
i have an old school dell inspiron 1525 with 2.0GHzx2 processor (dualcore) 2gb ram and other stuff.

i use ubuntu 10.4.1 lucid on it and it was before an hour i noticed a strange thing :S

the electricity blacked out, even though i had a fully charged battery, a black information showed that i have only 63 % battery available.

i booted into windows7 ( i have dual boot ) and it showed 98% battery left!

whats the matter?

did i do it wrong somewhere in installation? or does lucid have a bug?

regards

---

### Post by CharlesA on 2010-09-18
I believe Windows and Ubuntu measure battery life differently.

---

### Post by rahilm on 2010-09-18
> **CharlesA said:**
> I believe Windows and Ubuntu measure battery life differently.
i believe that too...
at one time:
ubuntu : 1 hr 5 min left
windows : 2 hr left

---

### Post by VanillaMozilla on 2010-09-18
Probably not a bug.

1. Batteries are flaky.  The time remaining may be erratic.
2. Maybe Ubuntu uses more juice, or expects to use more juice.
3. Maybe Windows is optimistic.

EDIT:  Oops, the values are in percent, not hours.  Therefore, 2 and 3 are probably wrong.

---

### Post by crackbuntu on 2010-09-18
whatever u say seniors :D but the thing is that even if UBUNTU is contended to use more of my battery life, it would reduce my battery time left. but the amount of charge in the battery is always same, wether in windows or ubuntu :|

how come ubuntu shows 64% and windows shows 98%?

---

### Post by WorMzy on 2010-09-18
Windows isn't exactly known for it's accuracy.

[http://xkcd.com/612/](http://xkcd.com/612/)

I'd be more inclined to believe Ubuntu's prediction. Chances are that the battery degraded over time and has lost some of it's capacity; Ubuntu is reading the battery's theoretical capacity and the current charge, and calculating that you have approximately 64% of a full charge left.

Windows, on the other hand, is probably making it up as it goes along.

*Note that I've never used a laptop, so the above is 100% speculation*

---

### Post by thatguruguy on 2010-09-18
Why assume it's a bug?

Make statements based upon evidence.  Run the computer on battery power and see how long it runs.  Recharge, and do it again.  Repeat several times, and then average out your battery life.  Then, you'll know which prediction is more accurate.

---

### Post by bodhi.zazen on 2010-09-18
> **thatguruguy said:**
> Why assume it's a bug?

Make statements based upon evidence.  Run the computer on battery power and see how long it runs.  Recharge, and do it again.  Repeat several times, and then average out your battery life.  Then, you'll know which prediction is more accurate.

+1 and it will depend on what activity you perform, so you will need to test it under the same conditions.

---

### Post by crackbuntu on 2010-09-18
i tested the battery performance on both ubuntu and windows:

on ubuntu : battery remaining : 63.2% (when fully charged)
runtime : ( nothing extra, basic system processes, a lan connection, general surfing on firefox, ram usage 13% of 2GB) about 59 minutes

on windows7 : battery remaining : 98.3% (when fully charged)
runtime : (all extra processes terminated, basic system processes, network service host running, lan connection, general browsing on firefox, ram usage 29% of 2GB ) 1hour and 45 minutes

now i am totally confused! how come ?

---

### Post by johnson094 on 2010-09-18
That's really interesting.  Wonder what's going on.  Try another test.  Disable screen saver, power saver, etc then boot up each to desktop and let it sit.  No surfing, no nothing.  Report back.
 
Thanks:)

---

### Post by VanillaMozilla on 2010-09-22
I tried it on an old Dell.  It seems to work fine.  Alternated booting Windows XP (from hard drive) and Linux (from CD).

73.7%  Ubuntu 8.10
69%    Windows
56%    Ubuntu 8.10
47.3%  Fedora 13

---


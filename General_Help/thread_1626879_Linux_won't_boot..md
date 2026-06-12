---
title: "Linux won't boot."
date: 2010-11-20
forum: General Help
---

### Post by questioned on 2010-11-20
Hi everyone. I have just recently installed Linux Lime along with windows 7 Home Premium. Before, there would be a menu asking me which operating system I would like to use. When I click linux it goes to linux and windows 7 goes to windows 7. Now when I click Linux, the black screen you get at the beginning shows a - (dash) constantly flashing on a black screen and won't boot to linux. This is normal as it does that for a second then boots. Now its stuck on that flashing dash on a black screen and won't boot. What do I do?

---

### Post by MooPi on 2010-11-20
When you get to the boot selection between Windows and Linux, choose the recovery console for Linux. From that point you can choose 
```
dpkg repair broken packages
failsafex fail safe graphics mode
root shell
```
There are other choices but these are probably what is needed.
From your description something is unresolved and is hanging boot. Try the first dpkg and see if that fixes the problem. If that doesn't do the trick go to failsafex and run a system update and upgrade . If that fails you can try the bootinfoscript [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/") Follow the instuctions on this page and report back the results.

---


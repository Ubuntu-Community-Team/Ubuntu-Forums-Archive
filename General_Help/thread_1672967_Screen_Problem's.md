---
title: "Screen Problem's"
date: 2011-01-21
forum: General Help
---

### Post by BoneFone on 2011-01-21
Hi community 

Im getting problems with my screen when I just installed Ubuntu 10.10 32Bit Operating System.

Problem: The screen flickers every once in a while.

Solution: ??

Im thinking its the fact that my Video card is the problem?

Its a Nivida Geforce GTX 460M VRAM 1.5GB 

CPU: Intel Core i7 740QM, 1.73GHz

Thanks Please Help as Soon as Possible!

---

### Post by ernz on 2011-01-21
Hi. Have you tried upgrading to proprietary drivers? You can do this by going to System > Administration > Additional Drivers. There should be a driver listed for your graphics. Hit "Activate" if it isn't already enabled and it will go away and automatically upgrade to prop. drivers after a restart.

If prop. drivers are already enabled, try disabling Compiz (although your graphics card really shouldn't be struggling). Run...
```
metacity --replace
```
...from the ALT + F2 run dialog. If this solves the flickering issue and you want to disable Compiz by default then go System > Preferences > Appearance > Effects > None.

Failing that, if it's possible you might want to try a different monitor or auto-adjusting your monitor. Might be a monitor issue?

---

### Post by BoneFone on 2011-01-21
Ok Thank You 

Hasen't Flicker'd Yet so I think that worked Thank You so Much!

---

### Post by ernz on 2011-01-21
Hi BoneFone. That's awesome. If it still seems fixed after a while, please mark this thread as "Solved" from the "Thread Tools" drop-down menu so other people can see the solution.

---


---
title: "monitor power off stops working after mplayer crash"
date: 2006-04-10
forum: General Help
---

### Post by mirkov on 2006-04-10
My lcd monitor suspends (powers off) just fine till mplayer crashes. After that, power management does not seem to work any more. I suspect that this is normal behaviour, because mplayer correctly prevents monitor from going into suspend mode, but if it does not terminates cleanly, the flag that prevents monitor from going into suspend mode does not get cleared (I kill mplayer by killall mplayer). I beleive xine behaves the same. Reboot corrects the problem, until the first mplayer / xine crash.

The question is, is there a way to tell the system after killing mplayer that inactivity monitor shoud be activated again?

I'm running Gnome, two independent desktops (monitor / tv) on one nvidia card.

---


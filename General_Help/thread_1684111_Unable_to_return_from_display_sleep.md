---
title: "Unable to return from display sleep"
date: 2011-02-08
forum: General Help
---

### Post by elklint on 2011-02-08
I'm running Ubuntu 10.10 64-bit with the latest ATI Catalyst drivers (11.1) on a desktop computer, and recently I've started having problems with turning the display on after it has gone to sleep.

If I've been inactive for a while, Ubuntu sends the display to sleep (it goes dark and the power diode starts blinking). When I try to wake it up again by moving the mouse or hitting the keyboard, nothing happens. I haven't been able to do anything to wake it up, except for forcing it to shutdown using the power button and then starting it up again.

Can anyone think of what might be happening here? Thanks.

---

### Post by sanderj on 2011-02-08
I have the same problem on my Ubuntu 10.04 64-bit with an ATI on-board GPU.

But: it only happens with recent kernels. So from the grub menu I always select one specific older kernel (2.6.31-21), and then I don't have this problem.

So, my suggestion to you: select an older kernel from the grub menu, and see if that is a workaround ...

---


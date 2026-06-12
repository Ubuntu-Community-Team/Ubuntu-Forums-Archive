---
title: "shutdown/restart problem"
date: 2010-09-19
forum: General Help
---

### Post by cwbar_1 on 2010-09-19
Using AMD Duron desktop.  Fresh install of Xubuntu 10.04.  Can turn computer on normally if I do "sudo shutdown -h now" from the terminal.   If using normal shutdown procedures, I have to press the "reset" button to boot system after shutdown.   Any ideas?

---

### Post by llamabr on 2010-09-19
I don't see the problem.  After you've shut down, you need to press the button to boot back up?

What other way is there?

---

### Post by cwbar_1 on 2010-09-19
OK. _Normally_ when I shut down the desktop, I use Menu>Logout>Shutdown. (all mouse clicks)  Then when I restart the computer, I press the "power" button, the DVD, HDD leds light up, I hear 1 "beep" and the system boots..But with the fresh install, the DVD , HDD leds light up, but no beep, and the system will not boot without pressing the "reset" button.
If I shut the system down from the terminal, using the correct shutdown commands, the next power up is normal.

I have 1 button for power and 1 button for manual reset.

---

### Post by sikander3786 on 2010-09-19
> **llamabr said:**
> I don't see the problem.  After you've shut down, you need to press the button to boot back up?

What other way is there?
I think he is talking about this.

> I have to press the **"reset"** button to boot system after shutdown

<snip>

---

### Post by cwbar_1 on 2010-09-19
In case anyone else has this problem, the solution was simple.  After looking up "beep" codes, I realized Xubuntu install had picked the incorrect keyboard. After switching to my keyboard,  (Microsoft Natural Elite) the system shuts down and boots correctly.

---


---
title: "Does preload slow down start up?"
date: 2009-08-19
forum: General Help
---

### Post by lian1238 on 2009-08-19
I'm feeling as if preload is actually slowing down my start up time.
That is, the time from when I press POWER until I can actually use my computer.
Since, preload loads files from HDD to RAM on startup, it's actually using more resources, isn't it?

Preload does speed up program start up time, but what about session start up time?

---

### Post by mcduck on 2009-08-19
Yes, it will slow your startup time. Your system has a lot more to do during the startup since in addition to normal startup tasks also it needs to load all the programs you are preloading. More work to do takes more time. :)

---

### Post by snek on 2009-08-19
What would be the best system-type to install preload on?
If it slows up boot time it might not be very handy for a machine which only gets turned on once in a while to use many different programs. But I can imagine it's quite handy for desktop machines which are put in sleep mode and only run a couple of apps like browser/email/etc..

Does it even have any use on a server with no X installed?

---

### Post by mcduck on 2009-08-19
> **snek said:**
> What would be the best system-type to install preload on?
If it slows up boot time it might not be very handy for a machine which only gets turned on once in a while to use many different programs. But I can imagine it's quite handy for desktop machines which are put in sleep mode and only run a couple of apps like browser/email/etc..

Does it even have any use on a server with no X installed?

If you use sleep, then preloading is useless, as once you have started the program first time it's already loaded into memory. Which is exactly the same thing preloading would do. If you just suspend the machine the program will stay in memory anyway.

In my opinion preloading is pretty much useless, apart from those people who define their computer's performance by clocking the time it takes for Firefox to start.. :D

But anyway, it works best in the situations where you regularly use certain programs, and shut down the computer when you are ready.

In theory the total time from powering on the computer to the moment when your program is loaded on desktop stays the same, preload or not. Preload just does part of starting the app during system startup instead of doing it after you have clicked the icon to start t. The work that has to be done is the same either way. But preloading programs you are not using will of course only waste time and memory.

---

### Post by HeadHunter00 on 2010-09-05
preload slowed down my pc as i remember it. instead of just preloading, i just created a tmpfs for all the applications i use often.

---


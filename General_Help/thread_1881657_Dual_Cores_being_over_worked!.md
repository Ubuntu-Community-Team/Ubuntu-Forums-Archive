---
title: "Dual Cores being over worked!"
date: 2011-11-15
forum: General Help
---

### Post by DeathByLinux on 2011-11-15
Hello,
       so I am back on the forums for a new problem that I am having with Linux. My dual cores are being over worked for the simplest things like surfing the web! When I view them in system monitor, I can see them reaching upwards of 100% on one process and 99% on the other. This is rediculous and I know this is not normal. The simplest tasks bogg down the entire system and make things choppy. It is especially excruciating when playing Adobe Flash.
 Any ideas?

-DeathbyLinux

---

### Post by HermanAB on 2011-11-16
Run top or htop to see what is really going on and kill the errant processes.

---

### Post by galvatron408 on 2011-11-30
never mind the cpu usage... pay attention to the load. you can see the load in the upper right hand corner. well, is it high?

cpu usage just means that the cpu is working and nothing more. if load is high, you're in trouble. well, not really, but it does mean that something may not be right or it may mean, you just need a more powerful machine.

---

### Post by bluexrider on 2011-11-30
if your CPU wasn't working you would have more of an issue. For exceptional load issues I would concern myself.

---

### Post by galvatron408 on 2011-12-01
> **bluexrider said:**
> if your CPU wasn't working you would have more of an issue. For exceptional load issues I would concern myself.

I'd tell you, but you are running windows, so it's not worth my time.

---

### Post by appier on 2011-12-01
Are you using xscreensaver?  If so, does this occur after the screensaver has just been disengaged?

---

### Post by 3rdalbum on 2011-12-01
> **galvatron408 said:**
> cpu usage just means that the cpu is working and nothing more. if load is high, you're in trouble.

If the CPU is running at 100% on both cores and all the person is doing is surfing the web, then there's definitely something wrong. The load is probably high too if the CPU is working non-stop.

HermanAB has the right idea: Run System Monitor or the "top" command in the terminal and find out what process(es) are using so much CPU power. When you find out, tell us. Or try killing it/them. But **DON'T UNINSTALL THEM** unless we tell you it's safe to do so.

---

### Post by killermist on 2011-12-01
Flash is horribly inefficient.
A couple flash-based ads can easily peg out a single core.
Facebook/Google+/Myspace flash games will run the CPU pretty hard too (possibly multiple cores in some cases).

A bunch of the desktop transition/animation stuff also sacrifices CPU usage to make things "prettier".

It could be that the distro you're using is just too heavy for the hardware you're using it on.

---

### Post by appier on 2011-12-01
> **3rdalbum said:**
> HermanAB has the right idea: Run System Monitor or the "top" command in the terminal and find out what process(es) are using so much CPU power. When you find out, tell us. Or try killing it/them. But **DON'T UNINSTALL THEM** unless we tell you it's safe to do so.

Agreed, there are a few processes I am constantly having to kill.  One is the Skyrocket screensaver after unlocking the desktop--it proceeds to take one of the cores up to 100% and stay there.  (The screensaver is worth the extra effort; my neighboring windows users just drool over this particular screensaver.)

I am curious which errant process(es) are causing the cpu to work so hard...

---


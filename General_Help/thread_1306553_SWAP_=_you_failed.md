---
title: "SWAP = you failed"
date: 2009-10-30
forum: General Help
---

### Post by gft55827 on 2009-10-30
this is not a request but a bug report. or whatever you call it.

Each time i go low on memory system is swapping it out. its ok, but why it doesnt restore it after i release real memory? this way much of my memory stay on hd, while i LAG really bad with all my memory unswapping when needed. Please fix this, perhaps a simple function wich do swap cleanup once per few seconds would suffic. Every lets say 5 seconds it will check if there is more than XX% memory freed, and if it is, unswap some data. Or maybe let it unswap upon process exit, just run this function then, would help much.

if this is not intended behaviour, then maybe its something wrong in my pc. ubuntu 9.04 amd64.

---

### Post by wildweathel on 2009-10-30
I've experienced a similar problem before.  My solution was to stuff my laptop with as much memory as it can hold, and that fortunately worked.  But since you're having issues with swapping, I'm willing to try to figure it out.  

1) Can you change the thread title?  I know you're frustrated, but something like "Swap thrashing after running X" is more likely to get love than "you failed."

2) How much memory do you have and what version of the kernel are you running?  Open a terminal (Applications -> Accessories -> Terminal), run
```
grep MemTotal /proc/meminfo ; uname -rvm
```
and copy the two lines it prints out.  For example, my computer gives:
```

MemTotal:        2060360 kB
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686

```

The first is the total amount of memory available for programs, the second identifies exactly which Linux kernel I'm running.

3) It would be extremely helpful if you can find a series of steps that makes your computer laggy.  That well help pin the problem down.

4) Further reading:

[list]
[*]How to write good bug reports.  The best way to get something fixed is a clear report of how to reproduce the problem. [http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)
[*]Ubuntu's bug-reporting procedures: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[*]Some work is currently under progress to improve Linux's swap behavior.  Note that these are *very* big bug reports, so you shouldn't comment unless you're sure you're information is helpful.  LP bug [#131094]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094") and Linux kernel bug [#12309]("http://bugzilla.kernel.org/show_bug.cgi?id=12309").
[/list]


For further help, I recommend posting in this thread.  I'm subscribed to it, and I'll do what I can to help.  (I'm happy to try running Jaunty with limited memory and see if I can reproduce what you're seeing.)

---

### Post by lykwydchykyn on 2009-10-30
That's primarily a kernel issue; I'm willing to bet the number of kernel developers that read Ubuntu forums is bordering on zero.

If you're not happy with the swap behavior of your system, there are some tweaks you can try; have a look at this:

[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---


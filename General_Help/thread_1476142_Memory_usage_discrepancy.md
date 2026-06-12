---
title: "Memory usage discrepancy"
date: 2010-05-07
forum: General Help
---

### Post by kernco on 2010-05-07
I've noticed lately that my system runs sluggish and traced the problem to the fact that my memory usage was reaching levels where swapping would occur.  The strange thing is that when I look at sysinfo, it will show I'm using something like 1.9/2.0 GiB of my memory.  But then if I run top or system monitor and look at the list of processes sorted by memory, I can clearly see that the column will not even come close to adding up to 1.9 GiB.

Is there some way that a process can be hidden from being shown in top or system monitor?  In both I can see very low level root processes like init and hald running, so it's not like I'm only seeing my own processes or something.  I'm a little worried that there's some malicious program running invisibly.  Even right after rebooting, sysinfo is already reporting that I only have 30% of my 2 GiB free.

Could it just be memory leakage?  Or would leaked memory still show up as belonging to a certain process?

---

### Post by scottku on 2010-05-07
What is the output of running the "free" command on the command line?

Most Linux machines will try to use available memory to cache files from the hard drive.  See: [http://serverfault.com/questions/9442/why-does-red-hat-linux-report-less-free-memory-on-the-system-than-is-actually-ava](http://serverfault.com/questions/9442/why-does-red-hat-linux-report-less-free-memory-on-the-system-than-is-actually-ava)

---


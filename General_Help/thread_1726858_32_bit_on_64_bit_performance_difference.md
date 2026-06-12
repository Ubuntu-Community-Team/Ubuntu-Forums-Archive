---
title: "32 bit on 64 bit performance difference?"
date: 2011-04-11
forum: General Help
---

### Post by blah... on 2011-04-11
Hello everyone, I am currently using the 32 bit version of Ubuntu on my 64 bit laptop. My question is, does using a 32 bit version on said hardware reduce its performance (i.e will battery life be reduced, system be under more load, etc.)?

---

### Post by mörgæs on 2011-04-11
You will find lots of threads on the 32/64-bit question here:

[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

Best is to ask in one of those, if you don't find the answer.

---

### Post by lithopsian on 2011-04-11
CPU load is noticeably increased if you have included code to address beyond 1GB which almost every kernel does.  Performance decreases for the same reason.  Details will depend on your exact CPU and amount of memory.

---

### Post by lithopsian on 2011-04-11
CPU load is noticeably increased if you have included code to address beyond 1GB which almost every kernel does.  Performance decreases for the same reason.  Details will depend on your exact CPU and amount of memory.

It doesn't really matter whether the CPU is 64 bit or not, but obviously on a 32 bit CPU there is no option to run native 64 bit code and get rid of the performance-sapping workarounds for addressing extra memory.

---

### Post by blah... on 2011-04-11
> **lithopsian said:**
> CPU load is noticeably increased if you have included code to address beyond 1GB which almost every kernel does.  Performance decreases for the same reason.  Details will depend on your exact CPU and amount of memory.

It doesn't really matter whether the CPU is 64 bit or not, but obviously on a 32 bit CPU there is no option to run native 64 bit code and get rid of the performance-sapping workarounds for addressing extra memory.I see, so I guess come 11.04 I'll reinstall Ubuntu to its 64-bit version. The reason I asked this question was because for some reason, running programs on Ubuntu would cause the CPU load to become very high, while running the same programs on Windows 7 (64-bit) such as Chrome wouldn't even have much of an effect on the CPU.

---


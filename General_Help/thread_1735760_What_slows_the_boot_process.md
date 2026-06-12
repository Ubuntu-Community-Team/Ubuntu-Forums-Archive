---
title: "What slows the boot process"
date: 2011-04-21
forum: General Help
---

### Post by sidewalkcynic on 2011-04-21
As I begin to install 11.04, I do as I always do, I set up my partitions in a different manner in the hopes that it will help make it all faster.

What I think happens is that the booting slows as the home folder gets larger and the files are fragmented - is that correct? Then what is the solution since there is no defragmentation for Linux - copy the home folder and then replace it back?

---

### Post by lithopsian on 2011-04-21
If your home folder is very badly fragmented then that could slow the boot process.  This would normally only be a problem if the partition became nearly full, otherwise Linux filesystems wouldn't fragment enough to cause big problems.  It is worth pointing out that the majority of file accesses during boot  are not to the /home directories and it would really have to be bad for  you to notice.

There are some utilities that can defragment Linux filesystems, but copying the whole lot is a pretty simple start.  If you have enough space then the copied directories will not be highly fragmented.

---

### Post by sidewalkcynic on 2011-04-21
Well, I notice after a fresh install the boot takes less then a minute, after about three days it seems to take about two minutes, then maybe here after six months since the last install it probably still takes a little more than two minutes - I'll give it a check, now, anyway.

---

### Post by sidewalkcynic on 2011-04-21
Oh, I cannot be anymore embarrassed!!!

I ran the start twice, and it only took a minute each time - never mind me and my quest for speed.

---


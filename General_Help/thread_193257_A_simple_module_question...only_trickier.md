---
title: "A simple module question...only trickier"
date: 2006-06-09
forum: General Help
---

### Post by keithjr on 2006-06-09
Okay, I've been struggling for a while with a [very specialized issue]("http://www.ubuntuforums.org/showthread.php?t=190142") that nobody seems to be comprehending (makes me feel a little better), but I have it down to one simple question...

If I have a self-compiled module, but for my kernel version, where do I put it so that I can modprobe it, load it, and make everybody happy and add it to my /etc/modules list for auto-loading?  Everywhere I put the object file (vt1211.o, an i2c chip variant) seems to do me no good.

A gift of a child's laughter for anybody who can answer...

---

### Post by zxee on 2006-06-10
Have you tried the directories in /lib/modules/2.6.15-20-386/kernel/drivers/?
I don't know which directory applies to the module you're trying to load but that's the place the modules "live". Hope that helps.

---

### Post by keithjr on 2006-06-10
Thanks for the idea, but that is kind of part of my question... how does modprobe KNOW where this particular module must live?

---

### Post by zxee on 2006-06-10
From 'man modprobe'  "modprobe intelligently adds or removes a module from the Linux kernel: note that for convenience, there is no difference between _ and - in module names. modprobe looks in the module directory /lib/modules/`uname -r` for all the modules and other files, except for the optional /etc/modprobe.conf configuration file and /etc/modprobe.d directory (see modprobe.conf(5))."  You can check out this man page here too: [http://www.die.net/doc/linux/man/man8/modprobe.8.html](http://www.die.net/doc/linux/man/man8/modprobe.8.html)

---


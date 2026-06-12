---
title: "Dumping Physical Memory (beyond 1048576)"
date: 2010-05-31
forum: General Help
---

### Post by mattseanbachman on 2010-05-31
I've been writing a simple C program that attempts to grab the contents of physical memory.  

From my sources after googling for some ten minutes, I came across the strange structure of /dev/mem, which I was referred to.  I had a simple program as follows to dump the contents of such out to a file (with redirection).  However, what happens is that after 1048576 bytes), everything is 0xFF! This cannot be.

I verified with hexdump that the same thing happens.  What is going on? Does linux allow application programmers to access the whole of physical memory by any easy means?

Also, a dmesg warning popped up that 

```
Program a.out tried to access /dev/mem between 101000->102000.
```Is some other program blocking my efforts? Or is this de facto disallowed?

I can follow up with the C code if it is desired.  Since not even hexdump can get past the set limit, I've decided not to include it for the time being.


Thanks,
Matt

---

### Post by BoneKracker on 2010-05-31
I would guess that is being caused by CONFIG_STRICT_DEVMEM=Y in the kernel configuration.  But that's a guess.

[http://cateee.net/lkddb/web-lkddb/STRICT_DEVMEM.html](http://cateee.net/lkddb/web-lkddb/STRICT_DEVMEM.html)

---

### Post by mattseanbachman on 2010-05-31
Thanks for that page.  Now I'll only need to find some way to turn that off...hopefully too that can be done without having to recompile the kernel or whatever.  I was mostly looking for a quick way to do some forensic work with the memory, dumping it and whatnot at specified intervals.  

Thanks for the nudge in the right direction.

---

### Post by BoneKracker on 2010-05-31
I seem to recall that there is (or was) a patch that makes a sysctl for that purpose, but I dont' think it was incorporated into the mainline kernel, because I don't see such a systcl.

Either way, you'd have to rebuild (to implement the patch or disable the option).

Like I said, though, I'm just guessing that this is what you're running into.  One thing you could do is check to see if that option is enabled in your kernel.  (If it's not, then this isn't the problem.  I think ubuntu enables CONFIG_IKCONFIG_PROC, so you could check /proc/config.gz for the option:
```
zgrep CONFIG_STRICT_DEVMEM /proc/config.gz
```
If it says "=n", then it's not enabled, and you can forget about this theory.

---

### Post by sdennie on 2010-05-31
If you are running on a 32 bit machine, it's also possible that /dev/mem is only presenting you with "low memory" (but, I don't know).  A question this technical may be better answered on something like lkml.  You will find a number of people around here that can give you theories to push in you the right direction about very low level things but, few, if any, kernel devs.

---

### Post by echo6 on 2010-07-06
You might be interested in this post [http://gleeda.blogspot.com/2009/08/devcrash-driver.html](http://gleeda.blogspot.com/2009/08/devcrash-driver.html)

You may find Volatility python project interesting for memory analysis, Linux memory analysis support is still in early development however.
[https://www.volatilesystems.com/default/volatility#overview](https://www.volatilesystems.com/default/volatility#overview)

There is also a project called foriana [http://hysteria.sk/~niekt0/foriana/](http://hysteria.sk/~niekt0/foriana/)

CONFIG_STRICT_DEVMEM=y is indeed the reason why you can't acquire more that the 1048576 bytes.  Gleeda demonstrates how it is possible to acquire above that but it effectively requires a kernel module/driver to do so, and uses the Red Hat /dev/crash driver.

This is not too dissimilar to how things are with other Operating Systems e.g. Windows 2k3 SP1 and above and of course MAC OSX (since Panther iirc) which removed /dev/mem altogether.

---


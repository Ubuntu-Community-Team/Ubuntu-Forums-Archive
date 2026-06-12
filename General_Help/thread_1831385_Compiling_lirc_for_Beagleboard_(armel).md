---
title: "Compiling lirc for Beagleboard (armel)"
date: 2011-08-23
forum: General Help
---

### Post by SuppoTaalasmaa on 2011-08-23
Hi,

I'm running Ubuntu on my Beagleboard xm, and everything is ok more or less. 

I want to build a server application, which would interface with my serial infra red transceiver. 
I'm now stuck when trying to compile lirc for my setup. 

I am running kernel compiled by Robert Nelson ([http://elinux.org/BeagleBoardUbuntu](http://elinux.org/BeagleBoardUbuntu)).
I realized that I will need also the sources for the kernel, to be able to compile lirc, so I downloaded also those. 
I was able successfully to recompile the kernel (to get the .config file), and now when I try to compile lirc, I seem to run into a strange error:
```
scripts/genksyms/genksyms: 1: Syntax error: "(" unexpected
```

The whole thing can be found also here [http://pastebin.com/x2w1VXcP]("http://pastebin.com/x2w1VXcP")

Is there some parameters I haven't set, to compile ? 
(Though my tool chain is downloaded from aptitude, and I can compile&execute my server application just fine)

This is my first beagle project, and I'm still new to the whole building kernel modules etc, so please don't hesitate to advice something simple I might have overlooked

Thanks in advance!

---

### Post by SuppoTaalasmaa on 2011-08-25
nobody ?

---

### Post by SuppoTaalasmaa on 2011-08-25
Interestingly I noticed that when I checked the kernel sources (which I compiled on x86 machine)

```

ubuntu@omap:/usr/src/linux/scripts/genksyms$ file genksyms
genksyms: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped

```

I wonder if this might be a problem ?
I'm trying to compile directly on the Beagleboard now...

---


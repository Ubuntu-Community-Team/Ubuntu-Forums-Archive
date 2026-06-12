---
title: "What system Architecture do i have?"
date: 2010-04-15
forum: General Help
---

### Post by marsters256 on 2010-04-15
I want to try Debian standard but before I can download and use I have to figure out what system architecture I have / platform I have so that I can download the one I need. 
Frustrating as the 'how to install' guide on the debian website offers no help as to how to find this out. 
Please help me .

---

### Post by wojox on 2010-04-15
Open a terminal and run:

```
uname -m
```

---

### Post by srs5694 on 2010-04-15
If you're not already running Linux, but are running a Windows system, chances are the x86 (aka i386) version will work. Most recent computers have x86-64 (aka AMD64 or EM64T) CPUs, which can use x86-64/amd64 distributions. I don't recall the exact Windows dialog boxes that reveal CPU information, but you can dig around until you find it and then check the Intel or AMD Web site to see if the CPU is 32-bit or 64-bit. If it's 32-bit, you can only use the x86/i386 distribution; but if it's 64-bit, you can use an x86-64/amd64 distribution.

If you're using a Mac, you'll have to know if it's Intel-based or PowerPC-based. I think that all Intel-based Macs use 64-bit CPUs, so you can use either x86/i386 or x86-64/amd64 distributions. If it's an older PowerPC computer, you'll need to look into a PowerPC version of any Linux distribution you want to try.

---

### Post by 3rdalbum on 2010-04-15
If your system can run Windows, then the i386  (x86) version will work. If it's a 64-bit processor inside your computer (such as an Intel Core 2 or Core i3/i5/i7 or AMD Athlon 64/Sempron64/Phenom), then you can use the "amd64" (x86_64) version.

If it's a PowerPC-based Macintosh, then you need the PPC build.

For anything else, you should check on Wikipedia what processor is used and what instruction set it uses.

---


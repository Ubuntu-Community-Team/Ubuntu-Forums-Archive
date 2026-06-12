---
title: "Find out which release I am running"
date: 2006-05-04
forum: General Help
---

### Post by embsupafly on 2006-05-04
What command in bash will tell me which release I am running... Hoary, Breezy...etc

---

### Post by nanotube on 2006-05-04
[QUOTE=embsupafly]What command in bash will tell me which release I am running... Hoary, Breezy...etc[/QUOTE]
```
cat /etc/issue
```

---

### Post by embsupafly on 2006-05-04
I am running an AMD Athlon 64 Processor 3800+ (/proc/cpuinfo) and it is running  kernel version 2.6.12-9-386, which is not a 64 bit kernel right?

I am having problems with the clock keeping time, it runs 2-3 times faster than normal and has been discussed here in the forums, should I update the kernel to a new version?

---

### Post by Ramses de Norre on 2006-05-04
That wont fix it, I'm still struggling with it too.. Haven't found a working solution yet (it seems the solutions are different for a lot of people..)

---

### Post by embsupafly on 2006-05-04
I have already started compiling a new version.... it won't hurt anything to try it right?

---

### Post by Ramses de Norre on 2006-05-04
You mean the newest one? Didn't try that, let me know if it fixes the problem. (I doubt it)

---

### Post by embsupafly on 2006-05-04
I am still in the process or recompiling the kernel, I chose Athlon from the Cpu type but also left the generic i386 support box checked. I was thinking that this would coexist with the Athlon selection, but all I have seen message wise in the compilation is arch for i386 nothing for 686 or athlon. Do I need to recompile with the generic 386 box unchecked?

---

### Post by embsupafly on 2006-05-04
compiling finished, in /usr/src the new headers and images read:

kernel-headers-2.6.12-custom_10.00.Custom_i386.deb

kernel-image-2.6.12-custom_10.00.Custom_i386.deb

I am assuming that with the i386 part of the filename that the Athlon support did not take?

I don't want to install these unless I know they are optimized for the Athlon

---

### Post by anthro398 on 2006-05-04
It seems like you've already got a working solution, but I found this useful tip that has worked with every Linux amd Solaris machine I've used.  

```
cat /etc/*elease*
```

---

### Post by nanotube on 2006-05-04
by the way, you don't really need to compile the new kernel - you can just try installing a kernel from the repositories. that's a much easier process. 

only if that one does not work you can try compiling from source... but i guess you might as well try what you got now. :)

---


---
title: "How do I find out my processor specifics?"
date: 2006-06-11
forum: General Help
---

### Post by miggl on 2006-06-11
Hi all,

I am trying to figure out what revision my AMD processor is, because VMWare won't play nice with creating 64-bit images on my host machine. Is there a tool or utility that will give me detailed information about my hardware?

The requirements from VMWare are the following: > VMware's virtual machine monitor has traditionally used segmentation to provide isolation between the guest operating system and the virtual machine monitor. This is necessary because the guest operating system and virtual machine monitor share the linear address space.

AMD
Segmentation support is missing from the initial AMD64 processors (that is, revision C and earlier) while running in long mode. As a result, AMD64 processors prior to revision D do not have an efficient mechanism for isolating the virtual machine monitor from 64-bit guest operating systems.

A limited form of segmentation was reintroduced in long mode, in revision D AMD64 processors. As a result, AMD64 processors must be revision D or later to run 64-bit guest operating systems.

Note: Because AMD Opteron and Turion processors do not ship in revision D, AMD Opteron and Turion 64 processors must be revision E or later to run 64-bit guest operating systems.
I want to verify my CPU's revision to make sure that that is indeed the problem, or that I compiled VMWare incorrectly.

Thanks!

---

### Post by rbalfour on 2006-06-11
$ cat /proc/cpuinfo

---

### Post by miggl on 2006-06-11
[QUOTE=rbalfour]$ cat /proc/cpuinfo[/QUOTE]
Thanks for the quick reply! Here are the results:```
mike@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 7
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 10
cpu MHz         : 2210.202
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 4423.27
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
```
How do I determine if it is revision C, D, or E?

---

### Post by miggl on 2006-06-11
Update:
I found this blog: [http://blogs.msdn.com/dangriff/archive/2006/03/19/555195.aspx](http://blogs.msdn.com/dangriff/archive/2006/03/19/555195.aspx)
However, it refers to this tool: [http://www.cpuid.com/](http://www.cpuid.com/) (CPU-Z). Unfortunately it is only available for windows.

---

### Post by miggl on 2006-06-11
Results:
Well, thank goodness for dual-boot. I ran CPU-Z on my windows partion, and come to find out, my CPU is codenamed CLAWHAMMER. According to various spec sheets this is a 130nm CPU, and not a 90nm CPU as required by VMWare. I guess it's off to the store now.

---

### Post by Ramses de Norre on 2006-06-11
Does vmware require a specific technology?? Is that normal?

---

### Post by miggl on 2006-06-11
[QUOTE=Ramses de Norre]Does vmware require a specific technology?? Is that normal?[/QUOTE]
It appears that VMWare requires 90nm CPU technology if you want to run 64-bit OS images on a 64-bit host server. If you run 32-bit images, it doesn't care. However, if you run 32-bit images on a 64-bit host server, you can't take advantage of 3D graphics accelaration hardware (your GPU(s)). In order for 3D acceleration to work you need to have the same image-type as the host-type is (i.e. 64-bit image on 64-bit host, 32-bit image on 32-bit host).

---


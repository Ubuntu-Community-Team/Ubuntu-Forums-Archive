---
title: "is hyperthreading on or no?"
date: 2010-07-29
forum: General Help
---

### Post by eppo on 2010-07-29
i have an ubuntu server running a Intel Xeon 2.4 quad core processor. i want to make sure that the OS is taking advantage of the HT of the cpu. when i do a cat /proc/cpuinfo i see 4 cpu's, should i see 8? also when i run top and hit 1, i see 4 cpu's, should i see 8 there also?
i've been doing some searching online about enabling HT, but the threads are from a long time ago, i see nothing recent. they say to enable SMP which i believe is already enabled:
2.6.28-17-server #58-Ubuntu SMP Tue Dec 1 22:13:36 UTC 2009 x86_64 GNU/Linux
anything else i could look at, or can someone shed some more light on this subject for me?
thanks

---

### Post by dcstar on 2010-07-31
> **eppo said:**
> i have an ubuntu server running a Intel Xeon 2.4 quad core processor. i want to make sure that the OS is taking advantage of the HT of the cpu. when i do a cat /proc/cpuinfo i see 4 cpu's, should i see 8? also when i run top and hit 1, i see 4 cpu's, should i see 8 there also?
i've been doing some searching online about enabling HT, but the threads are from a long time ago, i see nothing recent. they say to enable SMP which i believe is already enabled:
2.6.28-17-server #58-Ubuntu SMP Tue Dec 1 22:13:36 UTC 2009 x86_64 GNU/Linux
anything else i could look at, or can someone shed some more light on this subject for me?
thanks

Ubuntu will use whatever the hardware makes available to it, check any BIOS settings.

---

### Post by ankspo71 on 2010-07-31
> **eppo said:**
> i have an ubuntu server running a Intel Xeon 2.4 quad core processor. i want to make sure that the OS is taking advantage of the HT of the cpu. when i do a cat /proc/cpuinfo i see 4 cpu's, should i see 8? also when i run top and hit 1, i see 4 cpu's, should i see 8 there also?
i've been doing some searching online about enabling HT, but the threads are from a long time ago, i see nothing recent. they say to enable SMP which i believe is already enabled:
2.6.28-17-server #58-Ubuntu SMP Tue Dec 1 22:13:36 UTC 2009 x86_64 GNU/Linux
anything else i could look at, or can someone shed some more light on this subject for me?
thanks

Hi, I recommend installing 'htop'. Htop is a top-like command line program and I find it makes a great alternative to top. Top will only show all processors combined in one line, but htop will show multiple processors, including the hyperthreaded ones. 

+1 to the above reply. Ubuntu will automatically use hyperthreading if hyperthreading is enabled in your bios. I can turn mine on and off in my bios, and htop will show two or one processors respectively.

you can also run the command:
```
sudo lscpu
```
It will give you detailed info about your cpu(s)

Edit: I discovered another useful command:
```
sudo lshw -short
```
My single core CPU with hyperthreading enabled looks like this: 
> /0/2                 processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
/0/2/0.1             processor   Logical CPU
/0/2/0.2             processor   Logical CPU

---


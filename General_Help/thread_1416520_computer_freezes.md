---
title: "computer freezes"
date: 2010-02-26
forum: General Help
---

### Post by prabhanjan2906 on 2010-02-26
When ever i try to browse the net or try to watch a youtube video the firefox will stop responding and a grey screen will appear. Neither the mouse nor the keyboard will work. what could be the problem??? all these days it was going smooth all of a sudden this problem is occuring.
thanks in advance

---

### Post by Peter09 on 2010-02-26
Normally these sort of symptoms are likely caused by the graphics card.
What is the output of the terminal command
 
```
lshw -C video
```

---

### Post by prabhanjan2906 on 2010-02-26
*-display UNCLAIMED     
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=64 mingnt=8

---

### Post by Peter09 on 2010-02-28
If I remember rightly the Radeon Express 200 series is now not supported by ATI.

---

### Post by 3rdalbum on 2010-02-28
There are two good ways to check your memory:

1. Run Memtest from the GRUB menu. Run it overnight. If there are any errors, or if the computer is frozen when you come back to it, then you have faulty RAM.

2. Install Phoronix Test Suite and run the memory benchmarks. If your memory is faulty, the benchmarks will freeze the computer pretty quickly.

If the problem wasn't happening earlier, then it may well be a memory problem.

---


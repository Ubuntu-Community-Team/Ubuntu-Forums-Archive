---
title: "Ubuntu - 32-bit or 64-bit?"
date: 2011-06-09
forum: General Help
---

### Post by TheCadaver on 2011-06-09
Sorry if this is a noob question, :p

typing in uname -a in the terminal responds with 

Linux Neptune 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

Neptune's the computer's name. I built the computer myself, so, i could supply with cpu names anything i've used for it.

---

### Post by Frogs Hair on 2011-06-09
```
uname -m
```

---

### Post by HereInOz on 2011-06-09
Looks like 32 bit with a pae (Physical Address Extension) kernel to me.

---

### Post by 3Miro on 2011-06-09
> **HereInOz said:**
> Looks like 32 bit with a pae (Physical Address Extension) kernel to me.

+1. The first post lists 32-bit pae kernel.

PAE is a technology that will let you use more than 4GB of RAM on a 32-bit machine.

---

### Post by WorMzy on 2011-06-09
> **TheCadaver said:**
> Linux Neptune 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 **i686** GNU/Linux

The bolded part tells you which architecture you're using.

To compare, here's mine:

```
Linux sakura 2.6.38-ARCH #1 SMP PREEMPT Mon Jun 6 22:49:29 CEST 2011 **x86_64** Intel(R) Core(TM)2 CPU E8500 @ 3.16GHz GenuineIntel GNU/Linux
```

i386 is 32-bit
x86_64 is 64-bit

An easier way to check is to just run
```
arch
```

---

### Post by TheCadaver on 2011-06-10
So... I have i686. Everyone's mentioning i386. can someone explain to me what both of these things mean >.>

---

### Post by WorMzy on 2011-06-10
I don't speak fluent processor, but to my understanding, i486, i586 and i686 are all revisions of the i386 architecture. They all use the same IA-32 instruction set, meaning they're all 32-bit. i386 just gets used as the sweeping term for 32-bit processors, since it was the first one to use it (i286 was 16-bit).

---

### Post by 3Miro on 2011-06-10
> **TheCadaver said:**
> So... I have i686. Everyone's mentioning i386. can someone explain to me what both of these things mean >.>

i386 was the 386 standard from the early 90s (32-bit). i686 is like Pentium II or Pentium III form the late 90s (32-bit). Basically i386, i486, i586, i686 are all 32-bit.

AMD64 or x86_64 or EMT64 are the 64-bit architectures. AMD started it, so AMD64 is the most commonly used name in Ubuntu.

---


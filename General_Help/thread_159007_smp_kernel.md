---
title: "smp kernel"
date: 2006-04-12
forum: General Help
---

### Post by jturnbul on 2006-04-12
whats the difference between the regualr 686 kernel, and the 686-smp kernel???

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=jturnbul]whats the difference between the regualr 686 kernel, and the 686-smp kernel???[/QUOTE]
From Synaptic:

SMP (symmetric multi-processing) is needed if you have multiple processors.
Please read /usr/share/doc/linux-headers-2.6.12-10/debian.README.gz for
details

It makes both processors work.

---

### Post by mozetti on 2006-04-12
It also applies to single-processor systems when the Processor has either Hyperthreading (Pentium 4's) or Dual Cores.

**If you use a WiFi card with the Ralink RT2500 chipset, the legacy RT2500 drivers in Ubuntu don't work with the SMP kernel. A group is working on RT2500 drivers that will work with SMP kernels, but it's not at a final, released version yet.**

---

### Post by jturnbul on 2006-04-14
im running a centrino proc on my laptop, so I take it I dont need this kernel, yet thats the one Im using... How did I end up with it??? I dont recall ever having the option, and I upgrade via synaptic, so it must have decided I need it???

---


---
title: "Does Ubuntu supports Atom Hyper-threading?"
date: 2012-09-23
forum: General Help
---

### Post by mioimnida02 on 2012-09-23
Good Day! I installed fresh Ubuntu 12.04 64bit using WUBI. System Monitor detects two CPU. My Windows 7 also detects the same. 

I am using an Intel Atom N2100 and as far as I know this processor supports hyper-treading so I've run this command:

> sudo lscpu
and I get
> Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    2
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 54
Stepping:              1
CPU MHz:               1600.000
BogoMIPS:              3191.97
L1d cache:             24K
L1i cache:             32K
L2 cache:              512K
NUMA node0 CPU(s):     0,1


2 CPU * 1 core * 2 threads does that mean I have 4 cores? What does it mean? Why does System Monitor only detects 2 of it? Is there a possibility that I can enable hyper-threading? Thanks.

---

### Post by JRV on 2012-09-23
It is a single core hyper-threaded CPU.
You have one core running two threads.
If you run System Monitor it will say there are two CPUs.

---


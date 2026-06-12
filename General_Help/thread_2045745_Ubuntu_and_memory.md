---
title: "Ubuntu and memory"
date: 2012-08-21
forum: General Help
---

### Post by Mazate on 2012-08-21
Does anyone know how much memory Ubuntu CAN support?  In other words, what is the maximum amount of memory Ubuntu is made to support?

---

### Post by jwbrase on 2012-08-21
> **Mazate said:**
> Does anyone know how much memory Ubuntu CAN support?  In other words, what is the maximum amount of memory Ubuntu is made to support?

For 64-bit Linux, the limit is, according to [this]("http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00305.html"), 16 TB of RAM. (The hard limit imposed by the processor is 256 TB on current x86-64 implementations).

For 32-bit Linux, with PAE enabled, the limit is 64 GB of RAM, but each application can only use 3GB (32-bit applications running on 64-bit Linux are similarly limited, but IIRC the limit is 4GB instead of 3).

With PAE disabled, 32-bit Linux is limited to 4 GB of RAM, with each process being limited to 3 GB.

I believe there were some really old Linux versions that were limited to something like 800 megs of physical memory, but I believe that by the time Ubuntu came along those were long obsolete (and they certainly are now).

---


---
title: "Grub screen changed with each new kernel"
date: 2010-01-03
forum: General Help
---

### Post by mcastaneda68 on 2010-01-03
I have been learning about Ubuntu since 8.10. I have my two computers running dual boot (W7 + 8.04 & Vista + 9.10).

Sorry if this is a noob question, but I have noticed that each time there's a new kernel (now I have 2.6.31.16-generic), the grub OS selection screen adds 2 lines:
- One for the new kernel
- One for the new kernel - recovery mode

So, since I installed Karmic (2.6.31.14) Ubuntu Update has added 4 rows and shows:

- Windows
- 2.6.31.16
- 2.6.31.16 recovery
- 2.6.31.15
- 2.6.31.15 recovery
- 2.6.31.14
- 2.6.31.14 recovery
- Memtest
- Memtest

What is the rationale behinf this?
Why would I want to boot using the previous kernel versions?

In my laptop, it's GRUB 2. How can I eliminate the unused options?

Thanks!

---

### Post by tom.swartz07 on 2010-01-03
> **mcastaneda68 said:**
> I have been learning about Ubuntu since 8.10. I have my two computers running dual boot (W7 + 8.04 & Vista + 9.10).

Sorry if this is a noob question, but I have noticed that each time there's a new kernel (now I have 2.6.31.16-generic), the grub OS selection screen adds 2 lines:
- One for the new kernel
- One for the new kernel - recovery mode

So, since I installed Karmic (2.6.31.14) Ubuntu Update has added 4 rows and shows:

- Windows
- 2.6.31.16
- 2.6.31.16 recovery
- 2.6.31.15
- 2.6.31.15 recovery
- 2.6.31.14
- 2.6.31.14 recovery
- Memtest
- Memtest

What is the rationale behinf this?
Why would I want to boot using the previous kernel versions?

In my laptop, it's GRUB 2. How can I eliminate the unused options?

Thanks!

It keeps the old kernels just in case there is an error with the current one, or the new one doesnt work from the start- you could at least boot back in and fix it.

you could keep just one previous version and remove the rest - IE ~.14 from synaptic. Search for linux-image

---


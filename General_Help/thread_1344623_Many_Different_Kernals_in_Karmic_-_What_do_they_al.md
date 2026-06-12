---
title: "Many Different Kernals in Karmic - What do they all mean???"
date: 2009-12-03
forum: General Help
---

### Post by chewit on 2009-12-03
Its been quite a few releases since we have had a choice of kernels based on the CPU you have. Could please someone explain which kernel is for what CPU.

(Please note, for someone to answer my question, I'm using the 'image' as an explain, headers' has the same options)

[LIST]
[*]linux-image-2.6.31-15-386 (Linux kernel image for version 2.6.31 on i386)
[*]linux-image-2.6.31-15-generic (Linux kernel image for version 2.6.31 on x86/x86_64 - Default Ubuntu 9.10 kernel)
[*]linux-image-2.6.31-15-generic-pae (Linux kernel image for version 2.6.31 on x86)
[*]linux-image-2.6.31-15-virtual (Linux kernel image for version 2.6.31 on x86/x86_64)
[/LIST]

---

### Post by albandy on 2009-12-03
The 1st is for x86 (from 386 to any x86 cpu)
the 2nd is for x86_64 (for 64bit x86 cpu)
The 3rd is for x86 cpu with more than 3GB of RAM (PAE means Physical Address Extension)
The 4th is the linux kernel image for virtual machines

---


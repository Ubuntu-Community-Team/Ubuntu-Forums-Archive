---
title: "64bit vs 32bit graphics performance"
date: 2010-07-29
forum: General Help
---

### Post by mansourk on 2010-07-29
Hi,
Does installing 64bit instead of 32bit ubuntu has any influence on the performance of the system graphics? is there any difference between an integrated graphics and a non integrated one,a graphics card with dedicated graphics memory or shared memory?

---

### Post by dino99 on 2010-07-29
what is important is the real ram quantity available on the motherboard and on the graphic card. Generaly a graphic chipset is not very strong compare to a dedicated card.

About 32 or 64 bits: actually there is less bugs and issues with 32 bits, to use 4 G0 or more ram on your system, the best is to install kernel-pae which offer the 64 bits advantages without the issues

---

### Post by Bachstelze on 2010-07-29
> **dino99 said:**
> 
About 32 or 64 bits: actually there is less bugs and issues with 32 bits, to use 4 G0 or more ram on your system, the best is to install kernel-pae which offer the 64 bits advantages without the issues

You're five years behind, sir.

---

### Post by 3rdalbum on 2010-07-29
Your GPU does not really care whether your CPU is running in 32-bit mode or 64-bit mode, just like how your mouse does not really care.

---

### Post by Grenage on 2010-07-29
Damn right.

I usually choose x64, unless I'm on an old machine with a 32-bit CPU; the only reason I might use x32 is if I *knew* a critical app had major issues with x64 - and that's rare these days.

PAE is a dirty hack.

---

### Post by cascade9 on 2010-07-29
@ Bachstelze- yes, dino99 is a few years behind....

@ dino99- 4GB + PAE is slower than native 64bit. Even on 2GB of RAM, 64bit is faster, so "kernel-pae which offer the 64 bits advantages without the issues" is at least a little wrong. 

> **mansourk said:**
> Hi,
Does installing 64bit instead of 32bit ubuntu has any influence on the performance of the system graphics? is there any difference between an integrated graphics and a non integrated one,a graphics card with dedicated graphics memory or shared memory?

764bit vs 32bit video perfromance? No difference that I've seen. I've heard that there are differences in the media decoders, but as for any real world differnce, I'm yet to see it. 

Dedicated graphics memory vs shared memory- dedicated video memory doesnt use up your system RAM, and (unless you are comparing very old cards to very new computers) is faster all round. 

Onboard vs card- you will only find 'low end' intergrated GPUs.

---


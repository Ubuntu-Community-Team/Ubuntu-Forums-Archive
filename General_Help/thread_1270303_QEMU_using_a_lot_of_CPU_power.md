---
title: "QEMU using a lot of CPU power"
date: 2009-09-19
forum: General Help
---

### Post by blueshiftoverwatch on 2009-09-19
I installed QEMU and the graphical launcher so that I could run FreeDOS without installing it to a separate partition.

I'm running Ubuntu on a Pentium 4 processor and when I launch FreeDOS my processor usage monitor jumps from baseline (around 35%) to 99-100%.

I know that running something in a virtual environment takes more power than running it natively on it's own partition. But it shouldn't take anywhere near that much power to run a DOS based OS.

Anyone know why this is? If you need more information I'll do my best to provide it.

---

### Post by pxxc on 2009-11-19
Hi there,

I'm having the same problem: I've qemu over 8.10 and I'm trying to create an 9.10 image. I can't because it is to slow (it hogs the cpu) 

regards
PxC

---

### Post by 3rdalbum on 2009-11-19
Do you have an x86-based processor (e.g. made by Intel, AMD or Via?)

If so, then don't use Qemu; use Virtualbox.

Qemu emulates an entire CPU, which is very slow. I believe it emulates a Pentium Pro (I could well be wrong on this though). Virtualbox modifies instructions slightly and then passes them to your real CPU, making it very fast by comparison.

---

### Post by blueshiftoverwatch on 2009-11-19
> **3rdalbum said:**
> Qemu emulates an entire CPU, which is very slow. I believe it emulates a Pentium Pro (I could well be wrong on this though). Virtualbox modifies instructions slightly and then passes them to your real CPU, making it very fast by comparison.
Thanks for explaining. Since making this thread I've switched over to a 64 bit processor and am using Virtualbox.

Knowing what you just said, why would anyone use QEMU over Virtualbox? Can't VB do everything that QEMU does?

---

### Post by baxzius on 2010-06-29
I too have problem like you are facing friends.but at last i found a solution for this from a website .this site contains a patch which have to apply to the qemu source.you have to download qemu source.

 but be careful that in order to compile and make  the qemu source....
you need the follwing packages with you.

[B]zlib headers and SDL libraries.
[/B]thank you and Enjoy the Qemu Hacking.

**[http://www.miroslavnovak.com/qemu-brake_en.php](http://www.miroslavnovak.com/qemu-brake_en.php)**

---


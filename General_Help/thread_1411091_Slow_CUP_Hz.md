---
title: "Slow CUP Hz?"
date: 2010-02-19
forum: General Help
---

### Post by Tmora on 2010-02-19
Hi all

I am beginner of linux.
I tried
 cat /proc/cpuinfo
and found
 model name: Intel(R) Core(TM)2 Duo CPU P7450 @ 2.13GHz
 cup MHz: 800.000
Why CPU Hz is different between these two lines?
If someone knows it, please tell me.

Thank you.

---

### Post by DeMus on 2010-02-19
> **Tmora said:**
> Hi all

I am beginner of linux.
I tried
 cat /proc/cpuinfo
and found
 model name: Intel(R) Core(TM)2 Duo CPU P7450 @ 2.13GHz
 cup MHz: 800.000
Why CPU Hz is different between these two lines?
If someone knows it, please tell me.

Thank you.

You probably use a system which reduces the CPU frequency when the CPU is not, or just a little, used to save energy.
A slow CPU uses less energy than a fast running one, producing less heat this way, so the fan can spin slowly and make less noise. All benefits.

---

### Post by Tmora on 2010-02-19
Thank you DeMus.

So when I run some programs, 
cpu MHz rise up?
I cannot feel my PC is fast and
I am afraid my PC may be slower than the company says.

---

### Post by RJARRRPCGP on 2010-02-19
If you don't like that, then you must disable "C1E", "CState" and "Halt" in the BIOS.

Also disable anything that says "SpeedStep" in the BIOS.

---

### Post by rnerwein on 2010-02-19
> **Tmora said:**
> Hi all

I am beginner of linux.
I tried
 cat /proc/cpuinfo
and found
 model name: Intel(R) Core(TM)2 Duo CPU P7450 @ 2.13GHz
 cup MHz: 800.000
Why CPU Hz is different between these two lines?
If someone knows it, please tell me.

Thank you.

hi 
i think you don't need the BIOS.
have a look at the following link. 
[http://wiki.ubuntuusers.de/Prozessortaktung](http://wiki.ubuntuusers.de/Prozessortaktung)

it's in german but i think you will find the english version anywhere to.
ciao

---

### Post by Tmora on 2010-02-19
Thank you rnerwein

I tried to get something in the suggested page but I could not read German.
According your suggestion I will pick up some words in the page, google it, and find the English page.
Thank you very much.

---

### Post by GameManK on 2010-02-19
> **Tmora said:**
> Thank you DeMus.

So when I run some programs, 
cpu MHz rise up?
I cannot feel my PC is fast and
I am afraid my PC may be slower than the company says.
Yes, the CPU speed will go up when it's in use.

---


---
title: "AMD Catalyst Driver Install Advice"
date: 2012-08-17
forum: General Help
---

### Post by Petro Dawg on 2012-08-17
I'm downloading the correct drivers for my Laptop (Presario CQ62-209WM).  I'm hoping the new drivers will allow me to start using Ubuntu12.04 (instead of Ubuntu12.04 2D) with out my laptop heating up too much.  

This is my first time attempting to update drivers in Linux from sources other than the software center.  

I'm downloading **AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver** (which should correct for my ATI Mobility Radeon HD 4250 graphics chip) from the AMD Catalyst support site.

Are there any tips, or pitfalls, I should be aware of while trying to do the upgrade?  I want to be sure I do everything correctly from the start, so I can avoid an eventual whole system reinstall if things go too badly.  

I see a lot of posts about people having problems after installing new drivers, I want to avoid unneeded headaches.

---

### Post by overdrank on 2012-08-17
If I am not mistaken the graphics are AMD Accelerated Processors and the graphics drivers do not support the APU.

---

### Post by Petro Dawg on 2012-08-17
Well I tried the install, and CPU usage shot up( even in Ubuntu2D) and temps went up fast.  So reinstalled ATI/AMD drivers from the additional drivers program and  all is well in Ubuntu2D, but 3D still is not an option as laptop runs too hot in it.

---

### Post by QIII on 2012-08-17
The driver does support the APUs.  What is "hot" for a CPU isn't for an APU.  THE APU has everything on the same die.

However, heat can be an issue if you have dual ATI/ATI graphics or an Intel/ATI hybrid.

Does your machine have either?

---

### Post by Petro Dawg on 2012-08-17
> **QIII said:**
> The driver does support the APUs.  What is "hot" for a CPU isn't for an APU.  THE APU has everything on the same die.

However, heat can be an issue if you have dual ATI/ATI graphics or an Intel/ATI hybrid.

Does your machine have either?

My memory specs are as follows...

**Microprocessor  **2.1GHz VISION Technology from AMD with AMD Athlon II Dual-Core Processor for Notebook PCs P320 
**Microprocessor Cache** 1MB L2 Cache
**Memory**3GB DDR3 System Memory (2 DIMM)
**Video Graphics**ATI Mobility Radeon HD 4250 Graphics [B]
Video Memory[/B]Up to 1405MB 

Been having CPU heat issues for ubuntu for a while, been having to run Ubuntu2D with Jupiter runing in Power Saving Mode to keep temps in the lower 60's and below.  It was running 90+ degrees Celsius before making those changes.

---

### Post by QIII on 2012-08-17
Does the machine have a sticker that says "E2 VISION"?

---

### Post by Petro Dawg on 2012-08-17
> **QIII said:**
> Does the machine have a sticker that says "E2 VISION"?

Nope just "Vision"

---


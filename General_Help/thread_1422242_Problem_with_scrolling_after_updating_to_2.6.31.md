---
title: "Problem with scrolling after updating to 2.6.31"
date: 2010-03-05
forum: General Help
---

### Post by lautarox on 2010-03-05
I've upgraded my ubuntu kernerl's to 2.6.31, I'm using the x64 operating system. After upgrading all the time I scroll down like in Gedit, it goes extremely slowly, I've noticed that other programs have also been slow while scrolling content on them. I'm thinking it's because of the kernel upgrade because I can switch between installed kernels in the grub and the last one works perfectly.
Any suggestions?
Thanks in advance

---

### Post by ibuclaw on 2010-03-05
What graphics card + driver do you use?

---

### Post by lautarox on 2010-03-05
I have an ATI Raedeon HD Mobile 3700 series.
Thanks for the reply

---

### Post by ibuclaw on 2010-03-06
> **lautarox said:**
> I have an ATI Raedeon HD Mobile 3700 series.
Thanks for the reply

I can't find any precise reports of your issue, but what I do know is that issues with X generally boil down to a GFX driver issue.

If it works with the previous kernel, I recommend that you stick with it. Uninstall the newer one and lock the old one to prevent accidental upgrade.

Regards
Iain

---


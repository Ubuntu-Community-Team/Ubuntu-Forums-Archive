---
title: "Restart lock up"
date: 2009-08-26
forum: General Help
---

### Post by edheim on 2009-08-26
I recently installed Ubuntu within Windows XP to learn Linux and as an environment to learn C/C++. At the moment, I normally start the computer in Windows and then restart the PC to boot into Ubuntu. This part all works well. When I have finished working with Ubuntu, I do a restart to get back to Windows. I get back to the screen that shows the 2 boot options (Windows or Ubuntu) and then the PC locks up. At this point, I have to power down the computer.
 
My computer is a desktop and some hardware information is as follows:
 
CPU: Intel Pentium 4 630 - 3.0Ghz - (800FSB/LGA775/2MB Cache)
Motherboard: Gigabyte GA-8I945P Pro 
RAM: 2 GIG Corsair PC4200 DDR2
 
Windows XP Version 5.1 with Service Pack 3
 
I would appreciate any advice as to why this might be occuring.
 
Thanks, Edward

---

### Post by danwood76 on 2009-08-26
Some motherboards are a bit buggy.
You can try updating the BIOS, this may solve your issue.

Or you can simply do a cold boot each time (shutdown then power back up).

The problem with warm boots (no powerdown) is that all RAM areas can stay active which can cause issues when low level drivers (like BIOS and Boot loaders) want to access some areas and find data there.

---

### Post by edheim on 2009-08-27
> **danwood76 said:**
> Some motherboards are a bit buggy.
You can try updating the BIOS, this may solve your issue.

Or you can simply do a cold boot each time (shutdown then power back up).

The problem with warm boots (no powerdown) is that all RAM areas can stay active which can cause issues when low level drivers (like BIOS and Boot loaders) want to access some areas and find data there.
Thanks for your reply. Best Regards, Edward

---


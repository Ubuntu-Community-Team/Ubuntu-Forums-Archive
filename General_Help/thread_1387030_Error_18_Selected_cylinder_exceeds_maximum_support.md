---
title: "Error 18: Selected cylinder exceeds maximum supported by BIOS"
date: 2010-01-21
forum: General Help
---

### Post by dotweb on 2010-01-21
After rebooting my computer I get this error message:
Error 18: Selected cylinder exceeds maximum supported by BIOS

I suspect that this problem is related to GRUB and not to my HD?? even my HD is rather overloaded.

//Steen

---

### Post by efflandt on 2010-01-21
How old is your computer and how large is your hard drive?

If you boot from CD, what is the output of **sudo fdisk -l** (small L) and which partition are you trying to boot what Ubuntu version on?

PS: I have been using Linux long enough that I remember when the BIOS of some PCs did not support drives larger that 528 MB (that was MB not GB), and I had to install an extra card that did LBA to use all of a 540 MB drive.

---

### Post by dotweb on 2010-01-21
Hi, and thanks for your answer.
Just a few minutes before you made your replay to my thread, I had booted up on a Ubuntu CD. Out of the 160GB on the HD I only had 4 GB of free space.
I moved 20GB on to a USB drv. Emptied the recycle bin and rebooted - and wupti, it worked again. 
I cannot see where the problem should come from except maybe a full disk??? but then again no. 
It is a rather new pc, and the BIOS should support a 160GB disk (came with the pc) 
I will look a bit more into this problem and post more info.

Thanks for hearing in on this so fast :) great to know there are real people out there.

---


---
title: "Upgrade laptop to 4GB, Ubuntu 10.04 sees 3.3GB"
date: 2011-05-06
forum: General Help
---

### Post by UranUtan on 2011-05-06
Hi,

Using Ubuntu 10.04 x64. Laptop is HP 8430, CPU=T7200, 64bits, VT enabled. Video should probably ATI X1600.

Just upgraded from 3GB to 4GB. BIOS screen shows laptop has 4GB.  surpringly, within Ubuntu, System Monitor shows only 3.3GB.  What is the reason?

Thanks for any help.

---

### Post by l3vity on 2011-05-06
sorry, misread your initial post, managed to miss you were running 64bit already....

Have you tried a memory test from the grub boot menu?

---

### Post by Sef on 2011-05-07
Sounds like you are running a 32-bit system, which can only see 3.3 gb ram. If PAE is installed, then it can see up to 64 gb ram.

---

### Post by IanW on 2011-05-07
I suspect the missing RAM has been assigned to your oboard graphics card.

---

### Post by plucky on 2011-05-07
What does ```
uname -a
``` show?

---

### Post by UranUtan on 2011-05-10
uname -a

[B]Linux MyComputerName 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux
[/B]
I have checked with Memtest86+, the utility see only 3455 MB available. So then I guess that the remaining have been taken by the graphic chip. In the BIOS setting of the HP 8430, there is nothing that allow to set the quantity of RAM for the video card. Strange design.

---


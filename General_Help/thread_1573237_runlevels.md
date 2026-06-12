---
title: "runlevels"
date: 2010-09-12
forum: General Help
---

### Post by Obould on 2010-09-12
Hello,

can anyone tell me how I can boot my desktop (Ubuntu Lucid Lynx 10.04) into runlevel 1? Can you also tell me how to get from runlevel 1  back to the default (2) :p

Thanx in advance

---

### Post by Lateralis on 2010-09-12
When you get to the grub screen, highlight the kernel you wish to use and then hit 'e' to change kernel boot up options.  Highlight the kernel line on the next screen and hit 'e' to edit that, appending a 1 to the end of the line.

To change run level from a shell, I believe 

```

sudo telinit X

```

will do the job, where you replace X with whichever run level you want.

Question though: why do you want run level 1? :P

---

### Post by Obould on 2010-09-12
Hi, 

thanx for the quick reply. I am just experimenting, that is all. I am relatively new to Linux...

Greetz

---

### Post by Lateralis on 2010-09-12
No worries.  

Good luck experimenting!

---


---
title: "Kernel not booting - &quot;Booting the Kernel.&quot; message just sits there..."
date: 2010-04-20
forum: General Help
---

### Post by sab3156 on 2010-04-20
I am running Ubuntu 9.10 with a fresh install.  I installed kernel 2.6.26.8-rt16 the other day, and have gotten it onto grub2.  But sadly, it just doesn't seem to want to boot up...


With the boot option "acpi=off", it just hangs on a screen saying:

[INDENT]**Decompressing Linux... Parsing ELF... done.**
**Booting the kernel.**



**Kernel alive**
**kernel direct mapping tables up to 140000000 @ 8000-e000**
[/INDENT]

I'm not quite sure why this is so.  I did use **make menuconfig **and edit the config of this kernel a bit.

---

### Post by P4man on 2010-04-20
can you still boot the older, non rt kernels?
If yes, then well, its a problem with your customized kernel.
If no, then its a grub problem most likely.

edit: euh, hang on. That kernel is too old for Karmic. Karmic uses 2.6.31! 2.6.28 is for jaunty (9.04).

---

### Post by sab3156 on 2010-04-20
I can boot everything else except that kernel.

Are you saying then that I cannot use the 2.6.28.x kernel?  Cool.  I'll give the newer ones a try with the same settings and get back to you.  I was hoping to be able to use this one, but no big deal.  Thanks!

-sab3156

---


---
title: "Grub / Grub2 Install location"
date: 2010-10-02
forum: General Help
---

### Post by GMHilltop on 2010-10-02
I love tinkering with Ubuntu and Grub / Grub2.  I doing so I seem to remember with earlier distributions of Ubutnu that we'd install Grub to ..... hd0 .... I think it was.

Now I noticed that when choosing a location for it it comes up as .... /dev/sda 

I am pretty sure this is a dumb question, but .... It is still the same location right - MBR of the first drive, right?

Maybe a better question is .... Is there a reason it was changed?

---

### Post by psusi on 2010-10-02
Grub legacy used its own goofy notation for drives that was often problematic.  Grub2 uses the standard Linux designation.

---

### Post by GMHilltop on 2010-10-02
Thanks!

---

### Post by Rubi1200 on 2010-10-02
See here for more:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Includes an explanation of the differences between legacy-GRUB and GRUB2.

---

### Post by GMHilltop on 2010-10-02
Thanks for that - I have seen the link before.

It seems odd to me however that within the grub.cfg file that they are still using:

set root=(**hd0**,10)

Considering what was discussed above shouldn't it be:

set root=(**sda**10)

.... just wondering.

---


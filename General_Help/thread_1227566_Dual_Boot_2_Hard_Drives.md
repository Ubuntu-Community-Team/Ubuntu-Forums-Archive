---
title: "Dual Boot 2 Hard Drives"
date: 2009-07-30
forum: General Help
---

### Post by cgeorge1122 on 2009-07-30
Okay. I have a slight dilemma. I have two hard drives. One of which is dual booting Ubuntu/XP, the other is running Ubuntu. Up until a few hours ago they were in separate computers. I decided to combine the two and be able to multi boot the hard drives. Both have their own GRUB boot loaders and both can boot individually. The problem is trying to get the grub on hard drive 1 to be able to boot hard drive 2, and vice-versa. It gives me "Error 1: Filename must be either an absolute pathname or blocklist" when I try to boot the other hard drive.

Any suggestions?

---

### Post by SoftwareExplorer on 2009-07-30
I think it *might* be putting something like ```
title  Hard drive 2
root (hd1)
chainloader +1
``` in your first hard drive's menu.lst.

I'm not an expert, but if memory serves me well, it might do the trick.

---


---
title: "Grub configuration"
date: 2011-12-28
forum: General Help
---

### Post by ofnuts on 2011-12-28
The family computer has a dual boot WinXP+Ubuntu using Grub. It should default to WinXP... The Ubuntu was seldom used until now... The Grub menu used to be something like:

```

linux with kernel N
linux with kernel N (recovery mode)
memtest
memtest on serial
WinXP

```
However during last use, it got a new kernel so there are now two more items in the Grub list
```

linux with kernel N+1
 linux with kernel N+1 (recovery mode)
 linux with kernel N
 linux with kernel N (recovery mode)
 memtest
memtest on serial
WinXP

```
The problem is that the default WinXP was set using GRUB_DEFAULT=4 and that this didn't change when the new kernel was added so  the system now starts Memtest by default... 

I can of course change the GRUB_DEFAULT or uninstall the old kernel but the next auto-update will recreate the problem... so is there a way to make the WinXP order fixed (at 0?)?

---

### Post by BC59 on 2011-12-28
The simpler way to set default system is through StartUp Manager. Install it and choose the system to start.
No matter how many old kernels are existing.

---

### Post by Elfy on 2011-12-28
Part 2 of this might help - [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

---

### Post by ofnuts on 2011-12-28
Thanks both. Solved by the using the  *GRUB_DEFAULT="menu title"* syntax.

---


---
title: "Help me on boot selection option"
date: 2009-08-21
forum: General Help
---

### Post by Shijojoy on 2009-08-21
Hai friend,

in my system i have 3 operating system
Ubuntu 9.4
GOS 3.1 and
Windows 7
 the problem is while booting time system shows a 7-8 options like

[img]http://static.screencasts.ubuntu.com/20061204_installing_dual_boot.jpeg[/img]

how can i make it just three options for all 3 os?
any one can help on this

thanks in advance 
Shijo Abraham

---

### Post by pmlxuser on 2009-08-21
```

$ sudo cp /boot/grub/menu.lst menu.lst.bk
$sudo nano /boot/grub/menu.lst


```

read it carefuly and comment out the lines you don't want to see ...

---

### Post by Vaphell on 2009-08-21
it appears GOS entry is missing (unless it's not your grub :))
in case it's yours, you'll have to find out which partition it occupies and add proper entry to mentioned grub menu file.

---

### Post by pawhtiobo on 2009-08-21
Caution if you mess up your grub none of the OS will boot...backup first your menu.lst, then do the changes...and you should have a [supergrub boot disk]("http://www.supergrubdisk.org/"), in case things got the wrong way :-?...


see ya....

---


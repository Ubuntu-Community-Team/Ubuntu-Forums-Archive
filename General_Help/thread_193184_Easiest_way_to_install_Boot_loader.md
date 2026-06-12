---
title: "Easiest way to install Boot loader?"
date: 2006-06-09
forum: General Help
---

### Post by Grog140 on 2006-06-09
The idiot I am upgraded my XP partition via the Windows Vista Beta 2 disk. 

Being the moron I am, I failed to realize that M$ would install its own boot loader without asking and thus not letting me use my dapper partitition. 

So, what is the easiest way to go back to booting between dapper and Windows again? I would rather not format my computer.

---

### Post by xXx 0wn3d xXx on 2006-06-09
[QUOTE=Grog140]The idiot I am upgraded my XP partition via the Windows Vista Beta 2 disk. 

Being the moron I am, I failed to realize that M$ would install its own boot loader without asking and thus not letting me use my dapper partitition. 

So, what is the easiest way to go back to booting between dapper and Windows again? I would rather not format my computer.[/QUOTE]
[ This method is easy to use and it works. ](http://doc.gwos.org/index.php/Restore_Grub) It will re-install grub.

---

### Post by elamericano on 2006-06-09
LiveCD or rescue CD boot, then chroot to your installation and run grub-install [device]. This will rewrite the last grub menu you had. In other words, Grub won't have an entry for Vista. Maybe your previous Windows entry will work, but I always expect MS to be uncooperative every step of the way.

---

### Post by Grog140 on 2006-06-09
Well I am a slightly better situation since I would rather be stuch botting Ubuntu than Windows but I am still stuck.

How does M$ get away with this crap?

---


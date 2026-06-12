---
title: "Default OS"
date: 2010-05-03
forum: General Help
---

### Post by weaver4 on 2010-05-03
How do you change what the default OS is in the grub menu?

In the old grub it was pretty easy to edit the menu.lst file to point to the OS you wanted.

---

### Post by sisco311 on 2010-05-03
You can use [startupmanager]("apt://startupmanager") or edit the  /etc/default/grub file then run **sudo update-grub**.

See:
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
and
[uhelp]community/Grub2[/uhelp]

---

### Post by weaver4 on 2010-05-03
Thanks,

StartupManager is what I was looking for.  

If you go into Ubutnu-Software-Center and do a search for grub or grub2 it does not show up.  So I was having the hardest time finding it.

---

### Post by sisco311 on 2010-05-03
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---


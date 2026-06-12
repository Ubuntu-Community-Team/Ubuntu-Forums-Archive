---
title: "Grub"
date: 2006-02-07
forum: General Help
---

### Post by devel on 2006-02-07
How to change time-limit in grub to choose OS?

---

### Post by joft on 2006-02-07
Hi,

the timeout is usually configured in the file /boot/grub/menu.lst . Open it, search for the line "timeout" and change the value in the second column of this line.

---

### Post by Snoopy2052 on 2006-02-07
I think (IIRC) that the number given is the timeout in tenths of a second, so timeout=10 means 1 second.

---

### Post by joft on 2006-02-07
[QUOTE=Snoopy2052]I think (IIRC) that the number given is the timeout in tenths of a second, so timeout=10 means 1 second.[/QUOTE]

No, it's in seconds. /boot/grub/menu.lst itself tells us:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

---

### Post by devel on 2006-03-24
And how to change order of systems?

---

### Post by akshaysrinivasan on 2006-03-25
change the order in menu.lst

---

### Post by wjp.reg on 2006-03-25
If you want the **menu display** reordered, do as suggested above, but if you want to change the **default menu item**, then change it in menu.lst at the "default" line.  Numbering starts with "0".

Cheers

---


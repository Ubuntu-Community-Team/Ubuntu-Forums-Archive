---
title: "Ubuntu 10.10 doesnt start anymore."
date: 2011-03-29
forum: General Help
---

### Post by kanishkdudeja on 2011-03-29
When i start Ubuntu 10.10, im greeted with the following errors:
```

mount:mounting /dev on /root/dev/ failed: No such file or directory.
mount:mounting /sys on /root/sys/ failed: No such file or directory.
mount:mounting /proc on /root/proc/ failed: No such file or directory.
target filesystem doesnt have requested /sbin/init.
No init found. Try passing init= bootarg.
```

Any solutions ?

---

### Post by sas_man on 2011-03-29
I got the exact set of messages yesterday for version 10.04.  I'm only acknowledging your (and my) problem.  If I figure it out, I'll respond again.

---

### Post by kanishkdudeja on 2011-03-29
thanks a lot mate.

---

### Post by Grenage on 2011-03-29
Can you boot with a previous kernel? (I'm guessing not).
Do you have an external drive plugged in, but don't normally? (USB flash, etc).
Can you boot from the liveCD, then post the contents of grub.cfg and fstab?

They should be stored (on the drive) under:

/boot/grub/grub.cfg
/etc/fstab

---

### Post by kanishkdudeja on 2011-03-29
Well..when i start my system..i get a lot of kernel options..no natter what kernel i choose i get the same errors.

No external drive plugged it.

Will try to do the stuff you told from booting from the live cd.

---


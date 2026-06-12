---
title: "Can I dual-boot Ubuntu and Windows 7 without GRUB?"
date: 2010-08-07
forum: General Help
---

### Post by INH on 2010-08-07
I am running a dual-boot of Ubuntu 10.04 and Windows 7.  My current setup uses EasyBCD to pick between Ubuntu and windows.  If I pick Ubuntu, it then fires up GRUB, which then goes to Ubuntu.  My question is:  Can I skip GRUB altogether in the boot process?  I rather suspect that it's slowing things down a lot.  I've set the GRUB default OS timeout to 0, but it still boots slowly, which annoys me.  

Any way to skip GRUB entirely and use only EasyBCD for both OSes?

---

### Post by deserthowler on 2010-08-07
No,

Earl

---

### Post by INH on 2010-08-07
I see.  Thanks.  Is GRUB built into Ubuntu somehow?

---

### Post by ubunterooster on 2010-08-07
> **INH said:**
> I see.  Thanks.  Is GRUB built into Ubuntu somehow?
You _can_ skip the installation of grub but I see no reason *why*. Another bootloader you can use is LILO
[http://lilo.alioth.debian.org/](http://lilo.alioth.debian.org/)

---

### Post by Mark Phelps on 2010-08-08
> **INH said:**
> Any way to skip GRUB entirely and use only EasyBCD for both OSes?

Actually, you CAN.

It's not real easy to do, but if you read through the thread linked below, you will see the details:

[http://neosmart.net/forums/showthread.php?t=6808]("http://neosmart.net/forums/showthread.php?t=6808")

And, in future, you would do better going to the EasyBCD support forums when you have questions about THEIR product.

---


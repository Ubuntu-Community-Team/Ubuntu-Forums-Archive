---
title: "i8k &amp; conky"
date: 2010-10-29
forum: General Help
---

### Post by akernan on 2010-10-29
I have a Dell Inspiron 1564 with i3 processors, using 64-bit Meerkat.  I use conky to monitor my system.  When I use i8k to query stuff my system locks up.  Everything runs fine if I comment the i8k lines in conkyrc.  What am I doing wrong?  

I run sensors-detect from lm-sensors and nothing is found.

---

### Post by akernan on 2010-10-29
dmesg|grep i8k

[   15.384906] i8k: unable to get SMM Dell signature

sudo modprobe i8k

FATAL: Error inserting i8k (/lib/modules/2.6.35-22-generic/kernel/drivers/char/i8k.ko): No such device

I checked and the file is there.  Can I use i8k with my inspiron?

---


---
title: "Maverick Doesn't Boot"
date: 2010-12-29
forum: General Help
---

### Post by serlex on 2010-12-29
Hi,

I'm using 10.10 with kernel 2.6.35-24-generic.

Unfortunately after grub it gets stuck at:

```

couldn't find matching output script table
Checking batter state

```

Once stuck, I can go into tty1 and startx.

How do I find out what is causing this?

---

### Post by serlex on 2010-12-29
Had android udev rules in /etc/udev/rules.d/ 

removed and Ubuntu is working!

Spent 14 hours on this

---


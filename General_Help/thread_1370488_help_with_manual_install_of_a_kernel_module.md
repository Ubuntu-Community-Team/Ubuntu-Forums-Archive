---
title: "help with manual install of a kernel module"
date: 2010-01-02
forum: General Help
---

### Post by miatawnt2b on 2010-01-02
I grabbed and compiled the ipheth driver for my iphone which works great.  It's in my home directory and I can install the module with a simple 'insmod ipheth.ko'

I wanted this to load automatically at startup, so as root I made a directory /lib/modules/2.6.31-16-generic/kernel/drivers/ipheth and copied all the driver files into it.  I then edited the /etc/modules file and included ipheth.  However, the module doesn't install on boot.

Can someone tell me what I am doing wrong?

Thanks,
-J

---


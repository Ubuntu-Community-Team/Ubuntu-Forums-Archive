---
title: "Unable to compile driver"
date: 2009-12-09
forum: General Help
---

### Post by CharlesA on 2009-12-09
Hello,

I rebooted my box since it did a kernel upgrade. Now I cannot see my RAID array (which is usual after a kernel upgrade).

However, when I try to compile the driver for it. It's not working. I downloaded the driver form [here.]("http://www.highpoint-tech.com/usa/bios_rr2640.htm")

This is what I get:

```
root@thor:~/drivers/linux# make
Makefile:19: ../../../inc/linux/Makefile.def: No such file or directory
make: *** No rule to make target `../../../inc/linux/Makefile.def'.  Stop.
root@thor:~/drivers/linux#
```

Kernel version:

```
root@thor:~/drivers/linux# uname -r
2.6.28-17-server
root@thor:~/drivers/linux#

```

I don't know what's different, since after the last kernel upgrade, running** make install** worked fine. 

Thanks for any help.

---

### Post by Leppie on 2009-12-09
looks like you need to install the kernel headers.

---


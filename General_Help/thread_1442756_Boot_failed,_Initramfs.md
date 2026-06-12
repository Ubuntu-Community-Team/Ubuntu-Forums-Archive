---
title: "Boot failed, Initramfs"
date: 2010-03-30
forum: General Help
---

### Post by begui on 2010-03-30
So this morning I came into work to turn on my Ubuntu 9.10 Dell Latitude D820 only to find it would not boot into the Desktop but to the Initramfs. 

I'm assuming it was having trouble finding my root partition. so while in initramfs mode i was able to find+mount my root partition. 

Knowing where my root partition, i reboot the machine, got to the grub config by hitting e. and modified the line

linux /boot/vmlinuz-2.6.31.20-generic root=UUID={long hex} ro quiet splash

to 

linux /boot/vmlinuz-2.6.31.20-generic root=/dev/sda# ro quiet splash

Which worked. I was able to load the os. It works even after reboot. So, i'm assmuing that hex id was some how messed up. 

I tell ya.. if this were windows i would have to reformat the whole machine... 

Anyone else have this same problem?

---

### Post by grimv9 on 2010-04-03
Hey I just had the same sort of problem you had only that did not solve anything. I know exactly where my partition is but the command line keeps being reset back to uuID or whatever it is called.

---

### Post by begui on 2010-04-03
> **grimv9 said:**
> Hey I just had the same sort of problem you had only that did not solve anything. I know exactly where my partition is but the command line keeps being reset back to uuID or whatever it is called.



Were you able to boot back into your os by modifying your grub path at boot time? One thing you can probably do is set the path in the /boot/grub/grub.cfg file. You will have to change the permissions to edit it though.

---


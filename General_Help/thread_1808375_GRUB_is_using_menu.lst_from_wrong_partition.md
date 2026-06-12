---
title: "GRUB is using menu.lst from wrong partition"
date: 2011-07-20
forum: General Help
---

### Post by glue on 2011-07-20
I have 2 partitions (sda1 & sda3). Both have Ubuntu installed on them. GRUB is using the boot/grub/menu.lst on sda3. How do I get it to use the boot/grub/menu.lst on sda1?

Thanks

---

### Post by grahammechanical on 2011-07-20
From my own experience I would say that this happened when you did an update that included a new kernel and you ran the update in the Ubuntu on sda1 and then ran the update in Ubuntu on sda3. There are two ways to solve this.

1) always run updates on sda3 Ubuntu before running updates on sda1 Ubuntu. Then the next kernel update will put sda1 Grub menu.lst in action.

2) On sda1 Ubuntu install Grub Customizer. This is a great utility. Then after a kernel update you can use Grub Customizer on that partition to install that partition's Grub menu.lst into the MBR. You find it under File>Install to MBR. There is also a Select partition item in the file menu. I have never used that, so I do not know what it does.

Regards.

---

### Post by glue on 2011-07-20
> **grahammechanical said:**
> From my own experience I would say that this happened when you did an update that included a new kernel and you ran the update in the Ubuntu on sda1 and then ran the update in Ubuntu on sda3. There are two ways to solve this.

1) always run updates on sda3 Ubuntu before running updates on sda1 Ubuntu. Then the next kernel update will put sda1 Grub menu.lst in action.

2) On sda1 Ubuntu install Grub Customizer. This is a great utility. Then after a kernel update you can use Grub Customizer on that partition to install that partition's Grub menu.lst into the MBR. You find it under File>Install to MBR. There is also a Select partition item in the file menu. I have never used that, so I do not know what it does.

Regards.

It worked! Thanks a lot.

---


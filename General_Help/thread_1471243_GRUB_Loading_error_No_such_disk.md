---
title: "GRUB Loading error: No such disk"
date: 2010-05-03
forum: General Help
---

### Post by Nemisis7654 on 2010-05-03
Hi, 

I have a dual boot system with Windows 7 and Ubuntu 9.10. I booted into Ubuntu and started the process to upgrade to Ubuntu 10.04. When it was all finished, it restarted and attempted to boot into the GRUB load screen. However, I get this message: 

GRUB loading.
error: no such disck
grub rescue> 

I have no idea what to do right now. I'd greatly appreciate it.

---

### Post by phibit on 2010-05-03
Hi! I have a similar problem, but with Ubuntu running on a RAID1 array.

Have you tried booting into the LiveCD and doing the following? 

Assuming /dev/sda1 contains your Ubuntu installation:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by pehden on 2010-05-07
> **phibit said:**
> Hi! I have a similar problem, but with Ubuntu running on a RAID1 array.

Have you tried booting into the LiveCD and doing the following? 

Assuming /dev/sda1 contains your Ubuntu installation:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

I have this issue too, after I upgraded from 9.10 to 10.04 i did the grub set up a

---


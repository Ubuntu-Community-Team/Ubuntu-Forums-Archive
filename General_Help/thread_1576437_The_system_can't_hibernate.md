---
title: "The system can't hibernate"
date: 2010-09-17
forum: General Help
---

### Post by reverse_that on 2010-09-17
Hi all,

I have tried to hibernate the system through the menu kde -> leave -> hibernate.

The problem is that nothing happens and the system doesn't hibernate.

Do I have to configure something? How can I investigate and solve this issue?

Thanks.

fabio

---

### Post by plucky on 2010-09-17
> **reverse_that said:**
> Hi all,

I have tried to hibernate the system through the menu kde -> leave -> hibernate.

The problem is that nothing happens and the system doesn't hibernate.

Do I have to configure something? How can I investigate and solve this issue?

Thanks.

fabio

Check that your swap file is larger than the size of memory and that it is working.

Post output of ```
free -m
```

---

### Post by reverse_that on 2010-09-20
> **plucky said:**
> Check that your swap file is larger than the size of memory and that it is working.

Post output of ```
free -m
```

xxx@host05:~# free -m
             total       used       free     shared    buffers     cached
Mem:          3962       2693       1269          0         27         61
-/+ buffers/cache:       2604       1358
Swap:         3813        302       3511

Any idea?

fabio

---

### Post by plucky on 2010-09-20
> total used free shared buffers cached
Mem: [color=red]3962[/color] 2693 1269 0 27 61
-/+ buffers/cache: 2604 1358
Swap: [color=blue]3813[/color] 302 3511

Any idea?

Try increasing the size of you swap file to at least the size of your memory or more.

Also,changing the size of your swap partition will change the UUID of the partition,so you have to change the UUID in the /etc/fstab file and the /etc/initramfs-tools/conf.d/resume file.


Good Luck

---


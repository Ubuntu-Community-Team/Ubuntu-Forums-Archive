---
title: "dual boot between ubuntu and centos"
date: 2010-11-11
forum: General Help
---

### Post by oren tal on 2010-11-11
I have installed ubuntu,  then I installed centos.
I repatriate the hard. 
Centos did NOT recognize the ubuntu, so I reinstalled ubuntu.
Now Ubuntu don't recognize centos.

I have the following partitions in my hard drive:
 /dev/sda1 - etx4
/dev/sda3 - etx 3
/dev/sda4 - lvm 2
/dev/sda2 - extended 
/dev/sda3/ - linux swap

How do I make ubuntu to recognize centos?

---

### Post by Hippytaff on 2010-11-11
Try 
```

sudo update-grub

```

---

### Post by oren tal on 2010-11-11
> **Hippytaff said:**
> Try 
```

sudo update-grub

```

Thanks it solved the problem.

---

### Post by dino99 on 2010-11-11
olease change your thread to "solved" (thread tools above)

---

### Post by Hippytaff on 2010-11-11
Sorted :-D

---


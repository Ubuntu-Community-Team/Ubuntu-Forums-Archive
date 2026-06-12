---
title: "Re- creating dual boot without re-install"
date: 2011-01-07
forum: General Help
---

### Post by ptcat60 on 2011-01-07
When I attempted to create a dual boot computer with windows by accident I erased windows so I installed ubuntu as my operating system . I have since recovered the windows partition and want to create again a dual boot system. I have down loaded GaG is there a way to install it using Ubuntu 10-10,. 
I would prefer not to need to re-install Ubuntu?

---

### Post by dcstar on 2011-01-08
> **ptcat60 said:**
> When I attempted to create a dual boot computer with windows by accident I erased windows so I installed ubuntu as my operating system . I have since recovered the windows partition and want to create again a dual boot system. I have down loaded GaG is there a way to install it using Ubuntu 10-10,. 
I would prefer not to need to re-install Ubuntu?

How have you "recovered" the Windows partition?

If the partition is valid and on your hard disk then this will let Grub detect it:

```
sudo update-grub
```

---


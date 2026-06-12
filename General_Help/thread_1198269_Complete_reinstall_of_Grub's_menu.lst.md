---
title: "Complete reinstall of Grub's menu.lst"
date: 2009-06-27
forum: General Help
---

### Post by swerdna on 2009-06-27
Hi

When Ubuntu installs, it calculates a complete menu of operating systems to include other Linux and windows distributions and stores them in menu.lst. This creates a multiboot menu.

Over time my installed operating systems have changed. Ubuntu's multiboot menu is obsolete.

How do I get Ubuntu to completely recalculate and reinstall its menu.lst? 

Thanks
Swerdna

---

### Post by joshedmonds on 2009-06-27
I prefer to edit my menu.lst by hand, but if you want to update grub, try update-grub ;)

[http://man.he.net/man8/update-grub]("http://man.he.net/man8/update-grub")

It should be installed as part of the grub package, so just open a terminal and

```
sudo update-grub
```

and follow the man page instructions

---

### Post by swerdna on 2009-06-27
> **joshedmonds said:**
> I prefer to edit my menu.lst by hand, but if you want to update grub, try update-grub ;)

[http://man.he.net/man8/update-grub]("http://man.he.net/man8/update-grub")

It should be installed as part of the grub package, so just open a terminal and

```
sudo update-grub
```

and follow the man page instructions
Thanks for that. I've been editing by hand. The "update-grub" function looks good for kernels on the Ubuntu partition. But is there a function that will locate the Linux and windows kernels on the other partitions and create entries for those (I have six other operating systems on the drive and would like to be able to boot to those too from Ubuntu's menu.lst)?

---


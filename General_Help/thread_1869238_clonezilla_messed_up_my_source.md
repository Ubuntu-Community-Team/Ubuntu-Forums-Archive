---
title: "clonezilla messed up my source"
date: 2011-10-25
forum: General Help
---

### Post by Gatemaze on 2011-10-25
Hi,

I have two external drives, one of them had a healthy ubuntu system. I used the clonezilla cd to clone the ubuntu hard drive to another external hard drive. Now, I cannot boot from the source. The files to the target seem to have copied...

More detail... I can get to grub menu but nothing really boots... I've tried from a third pc with ubuntu
```

grub-install --root-directory /media/external /dev/sdb

```
I tried
```

sudo update-grub -o /media/external/boot/grub/grub.cfg

```
and created obviously the local machines kernerls too and the external drive ones... still cannot boot...

any help?

thanks!

---

### Post by Gatemaze on 2011-10-25
Managed to resolve it so closed. Still that clonezilla messed up the source disk is really concerning and annoying.

---


---
title: "Removing linux kernel image."
date: 2011-04-24
forum: General Help
---

### Post by bunny1 on 2011-04-24
Other than the linux kernel image I am using is it ok to remove the others I have and thus gain more disk space ? I only have a small asus 900 netbook.

---

### Post by Rubi1200 on 2011-04-24
Hi and welcome to the forums :-)

Yes, you can but it is advisable to keep at least one older kernel for troubleshooting purposes.

This link has information on how to remove older kernels:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by KegHead on 2011-04-24
Hi!

You can, but it's a good idea to keep one version behind should you need it.

You can update your kernel;

sudo apt-get update

sudo apt-get install linux-image -f

Restart to take effect.

KegHead

---

### Post by bunny1 on 2011-04-24
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Yes, you can but it is advisable to keep at least one older kernel for troubleshooting purposes.

This link has information on how to remove older kernels:
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

Thanks so much for that it worked a treat but it made my palms sweat with nerves a bit doing it lol. Can I also remove the kernel header files related to the Linux kernel images ?

---

### Post by Rubi1200 on 2011-04-24
> **bunny1 said:**
> Thanks so much for that it worked a treat but it made my palms sweat with nerves a bit doing it lol. Can I also remove the kernel header files related to the Linux kernel images ?
Yes, you can remove them. For each kernel image there should be 2 header files. In other words, when you remove an older kernel you are getting rid of 3 files in total.

Another thing that may interest you is a nice GUI application for organizing the GRUB menu:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---


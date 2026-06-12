---
title: "Removing from boot loader."
date: 2010-02-13
forum: General Help
---

### Post by eranga1988 on 2010-02-13
I have installed PAE kernel.so i tried to remove the old kernel from the boot loader and succeeded.but by a mistake i have installed another generic kernel which actually doesnt work.it was installed by giving a wrong image number(2.6.31-14) when uninstalling  the old image.i tried several times with a command like "sudo aptitude remove linux image-2.6.31-14-generic" (actually i dont remember the correct command now.)
so could u pls help me to remove 2.6.31-14-generic from the boot loader?
Thanx!!!

---

### Post by eranga1988 on 2010-02-13
Can any body pls help me???

---

### Post by lenoirrichelieu on 2010-02-13
You mean at this moment you have more kernels as options in grub menu and want to remove one?

---

### Post by eranga1988 on 2010-02-13
> **lenoirrichelieu said:**
> You mean at this moment you have more kernels as options in grub menu and want to remove one?

actually yes.i have installed PAE kernel.so i removed old generic kernel.but by a mistake i have installed a name of a generic kernel to the boot loader which doesnt work.it just appear on the boot loader.i wanna remove this name from the boot loader.

---

### Post by flippo on 2010-02-13
This page should be of use to you, 9.10 comes with grub2 by default:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---


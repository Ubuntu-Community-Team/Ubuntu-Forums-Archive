---
title: "What happens if I delete all kernel images?"
date: 2011-08-24
forum: General Help
---

### Post by KingA on 2011-08-24
As the title says, what happens if I delete all the linux kernel images? Would I make my linux OS useless ?

It never happened to me, but I'm curious. Is a kernel image possible to be rebuilt ?

---

### Post by oldfred on 2011-08-24
Welcome to the forums.

You will not be able to reboot. When you delete the kernel you are running it is not fully deleted since you are using it. But once you reboot it will be gone and you can not reboot.

You can use a liveCD and chroot into your system and run a set of update and download the most current kernel. 

For every system you have installed you should have a liveCD or Windows repairCD/USB of the same version. Then you have the capability of making repairs. I also like to have one or two other rescue CDs just in case.

---

### Post by sisco311 on 2011-08-24
EDIT: D'oh! oldfred beat me to it. :)

You won't be able to boot into the linux installation.

In case it happens, you can boot a Live CD/USB, chroot in your installation and reinstall the kernel.

---

### Post by elliotn on 2011-08-24
you can delete old kernels you don't use just as mentioned ensure your not deleting the one you use

---


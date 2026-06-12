---
title: "Auto boot to old kernel"
date: 2010-04-24
forum: General Help
---

### Post by primetime34 on 2010-04-24
I have updated to kernel 2.6.31-20.  However, it is very unstable on my laptop.  I still have kernel 2.6.31-14 on my laptop.  How can I get Ubuntu 9.10 to automatically boot to 2.6.31-14 which works great? I'm using Grub2.  Thanks.

---

### Post by rnerwein on 2010-04-24
hi
all the steps below you have to run with root permissions ( sudo )
you have to edit the file /etc/default/grub and change the entry: GRUB_DEFAULT=0 to the value where your old kernel
apears in the grub menue - e.g.

0 -> kernel 2.6.31-20
1 -> windoof 7
2 -> kernel 2.6.31-14

you have to set the value to ---> 2
save the file and run:

/usr/sbin/update-grub

ciao

---

### Post by primetime34 on 2010-04-24
Is there a way to look at the numbers you reference?  I think the old kernel is #3 in the list, but I don't know.  Is there a way to check?  I don't normally see the grub menu, only when the computer doesn't boot up right.  Thanks.

---

### Post by sdennie on 2010-04-24
If you hold down shift while your machine boots, you can see the grub menu.  Another option is to look in /boot/grub/grub.cfg and search for "menuentry".  Both methods show how grub will number the kernels.

---

### Post by primetime34 on 2010-04-24
Works great...thanks!!

---


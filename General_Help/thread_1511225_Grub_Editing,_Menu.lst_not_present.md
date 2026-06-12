---
title: "Grub Editing, Menu.lst not present"
date: 2010-06-16
forum: General Help
---

### Post by p52ntwrk on 2010-06-16
Xubuntu: Grub Editing, Menu.lst not present

ver: 10.04 Lucid Lynx
performed update
Grub now features Redundant options upon boot
similar to the following

Ubuntu, kernel 2.6.32-22
Ubuntu, kernel 2.6.32-22 (recovery mode)
Ubuntu, kernel 2.6.32-21
Ubuntu, kernel 2.6.32-21 (recovery mode)
Ubuntu, memtest
Ubuntu, memtest 


/boot/grub/menu.lst does not exist

is grub loading the .img files from /boot?
example: both located /boot
initrd.img-2.6.32-21-generic
initrd.img-2.6.32-22-generic  


insignificant but would like to slim grub
to avoid much arrowing to my other systems

any ideas appreciated
thankyou

---

### Post by bmbigam on 2010-06-16
try
/boot/grub/grub.cfg
this is the file that replaced menu.lst

---

### Post by philinux on 2010-06-16
> **bmbigam said:**
> try
/boot/grub/grub.cfg
this is the file that replaced menu.lst

Don't edit that file it is system generated. Either  instal startupmanager, or remove old kernels via synaptic and click the link below for Grub2.

---


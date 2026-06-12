---
title: "dual booting mannually"
date: 2010-04-25
forum: General Help
---

### Post by nos09 on 2010-04-25
how to dual boot os manually.
i want to install backtrack 4 and ubutnu side by side. and i want to konw how to do it manually without destroying my data if possible !?

---

### Post by dino99 on 2010-04-25
you need 4 partitions:

1 - your first distro
2 - your second distro
3 - your /home partition for own work
4 - your swap ( max twice physical ram)

so you need to prepare your hdd(s) with gparted as ext3
then install the distro and the bootloader (grub) on the linux mbr partition. When installation is ended, reboot on linux, then into console:

for lucid with grub2
- sudo grub-mkconfig
- sudo update-grub

or with grub1
 - sudo update-grub

---


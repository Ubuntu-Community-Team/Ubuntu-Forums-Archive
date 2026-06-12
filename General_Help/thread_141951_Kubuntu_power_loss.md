---
title: "Kubuntu power loss"
date: 2006-03-09
forum: General Help
---

### Post by demouskavitch on 2006-03-09
I just installed kubuntu on a partition  aside from WindowsXP.  My computer will now completely turn off (requiring uplugging and switching the power supply) randomly.  Ive only had Kubuntu up for a few hours and this has happened three times.  When I ran WindowsXP this never happened:  any ideas for a fix?  

(I am obviously very naive with Linux!)

---

### Post by qb4ever on 2006-03-09
If windows xp doesn't randomly reset, it could be a buggy acpi bios. How old is the computer?

---

### Post by demouskavitch on 2006-03-09
The computer is old, about 4 years.  Would I change the bios?

---

### Post by towsonu2003 on 2006-03-09
try another distro?

---

### Post by qb4ever on 2006-03-09
That too ^^


[QUOTE=demouskavitch]The computer is old, about 4 years.  Would I change the bios?[/QUOTE]


Open up your menu.lst from a terminal:

sudo gedit /boot/grub/menu.lst

then find the kernel line and add to the end:

kernel		/boot/vmlinuz-2.6.15-ck5 root=/dev/hda1 ro ***_acpi=off_***

---


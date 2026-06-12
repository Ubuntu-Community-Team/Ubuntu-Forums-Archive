---
title: "GRUB Help"
date: 2006-04-13
forum: General Help
---

### Post by shmuel on 2006-04-13
Hi

I am about to install fresh copies of XP and Ubuntu onto my computer. When installing Ubuntu is there anyway to disable GRUB from the beginning, when it gives the option, and still access Windows, as I want to install GRUB on the Windows partition. Does the install make Ubuntu the default OS?

Thanks for your help

---

### Post by Darkriser on 2006-04-13
when you install Ubuntu AFTER windows xp, GRUB will ercognize both OS and create a boot menu for both (if installed in MBR).

anyway, during installation you are asked where to install grub. you can boot from MBR (recommended), you can boot from floppy, etc...

---

### Post by shmuel on 2006-04-13
Thanks for your help...

How would I go about making Windows the default OS?

Thanks

---

### Post by Darkriser on 2006-04-13
once ubuntu installed, type in console:

'sudo gedit /boot/grub/menu.lst'

it's a plain text file used for boot menu configuration. there you'll find a list of all items of your boot menu, as well as the default item number (note that items are numbered from 0). it's very user-friendly and quite simply readable, don't worry about it....

---

### Post by shmuel on 2006-04-13
Thanks for your help...

Will do it now

---


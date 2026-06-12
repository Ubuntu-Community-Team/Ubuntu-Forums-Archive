---
title: "i commentd out root in /etc/passwd - help!!"
date: 2009-08-31
forum: General Help
---

### Post by confused_user on 2009-08-31
Hi, i did something very stupid last night, i accidentally set a root password in my 9.04 install.  I realised what i had done so went and commented out root in /etc/passwd thinking that this would disable root logins.

It did, but it also prevents me from using sudo.  I basically cant do anything on this machine anymore.

Cab anyone help me out with a way of uncommenting root in my /etc/passwd file?

also, this is compounded by my usb keyboard and usb mouse not working in X anymore which i think is related.

---

### Post by SlugSlug on 2009-08-31
you could do it from a live cd  or boot to recovery and you will be logged in as root

---

### Post by mechdave on 2009-08-31
In order to fix it you need to boot into a single user mode. The mode is the recovery option in grub. It looks similar to this -->

Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

Boot into that to a command line and then use passwd root to change the root password. Or even use nano (I think it works in single user mode), to uncomment your commented line in /etc/passwd

Good luck,
MechDave

---

### Post by confused_user on 2009-10-23
> **mechdave said:**
> In order to fix it you need to boot into a single user mode. The mode is the recovery option in grub. It looks similar to this -->

Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

Boot into that to a command line and then use passwd root to change the root password. Or even use nano (I think it works in single user mode), to uncomment your commented line in /etc/passwd

Good luck,
MechDave

hi, sorry i forgot to respond here,that worked well thanks:guitar:

---


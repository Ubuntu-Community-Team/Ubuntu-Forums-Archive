---
title: "boot up problem"
date: 2009-11-05
forum: General Help
---

### Post by tempus on 2009-11-05
Help,
I tried to install Fedora next to ubuntu and for some reason it now boots directly into fedora bypassing ubuntu. How can i get it to boot into ubuntu or give the option of a dual boot?
thanks.  :popcorn:

---

### Post by Giblet5 on 2009-11-05
Well, you have to choose which one will control the boot menu, edit that OS's grub config, then remove grub on the other OS.

Grub's like "Highlander": there can be only one.

So, which one will you spend more time using? That's probably the one that should control the grub menu.

---

### Post by tempus on 2009-11-05
> **Giblet5 said:**
> Well, you have to choose which one will control the boot menu, edit that OS's grub config, then remove grub on the other OS.

Grub's like "Highlander": there can be only one.

So, which one will you spend more time using? That's probably the one that should control the grub menu.

thanks giblet,
would modify it if i could find the menu!!

---

### Post by rkham11 on 2009-11-05
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
if you don't understand grub well, this is an easy fix. 
Just install this to a flash drive and boot from it and you can choose which partition to boot from
I'ts very easy to use

---

### Post by tempus on 2009-11-06
> **rkham11 said:**
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
if you don't understand grub well, this is an easy fix. 
Just install this to a flash drive and boot from it and you can choose which partition to boot from
I'ts very easy to use

thanks for the link.  solved the problem by re-installing Ubuntu from scratch. I remember doing this with MS products.......:D):P

---


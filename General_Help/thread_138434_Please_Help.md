---
title: "Please Help"
date: 2006-03-01
forum: General Help
---

### Post by Fred G on 2006-03-01
I'm new to linux and need some help.
I installed Ubunto on my Thinkpad t41p, after the install the grub loader gave me an error 17 and xp or Ubunto would not boot. So I reinstalled Ubunto and used the Lillo boot loader, now the Ubunto loads great but there is never an option to boot XP.

---

### Post by seankann on 2006-03-01
Check your lilo.conf file.. there should be something pointing to your windows partition

---

### Post by Fred G on 2006-03-01
how do I do that?

---

### Post by seankann on 2006-03-01
try doing locate lilo.conf

if it says command not found

sudo apt-get install slocate

then do sudo updatedb

then try doing locate lilo.conf

most likely your windows partition is commented out

---

### Post by Kevinator on 2006-03-01
But Ubuntu (5.10) uses GRUB by default, not LILO.

---

### Post by Fred G on 2006-03-01
Ok it shows me 
 /etc/lilo.conf

what do I do with that

As you can tell Im new to linux

---

### Post by seankann on 2006-03-02
ya why are you using lilo? grub is a lot better

---


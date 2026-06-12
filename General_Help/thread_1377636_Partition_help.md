---
title: "Partition help"
date: 2010-01-10
forum: General Help
---

### Post by ubudog on 2010-01-10
Hi, I have 3 versions of Ubuntu installed and Windows XP.  If I remove the 3 versions of Ubuntu, that will make windows boot automatically, right?

---

### Post by SuperSonic4 on 2010-01-10
Nope, it will delete grub leaving you unable to boot windows without either a XP recovery CD/partition

---

### Post by ubudog on 2010-01-10
> **SuperSonic4 said:**
> Nope, it will delete grub leaving you unable to boot windows without either a XP recovery CD/partition

Ok, so does it read the grub config off of a certain Ubuntu install?

---

### Post by ubudog on 2010-01-10
I think the 9.04 install has the grub config.  So can I delete all the other Ubuntu installs and leave that one?

---

### Post by KrazyPenguin on 2010-01-10
> **ubudog said:**
> Hi, I have 3 versions of Ubuntu installed and Windows XP.  If I remove the 3 versions of Ubuntu, that will make windows boot automatically, right?

You want to boot windows automatically then just make it default in grub.
Then you can set timeout to zero, and hide grub and it will boot right into XP even though ubuntus and grub are still there.

---

### Post by ubudog on 2010-01-10
Thanks for the help! ;)

---

### Post by lindsay7 on 2010-01-10
If you have the xp install disk, you can just re-set the windows mbr.


[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---


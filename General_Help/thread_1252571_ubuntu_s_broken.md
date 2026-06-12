---
title: "ubuntu s broken"
date: 2009-08-29
forum: General Help
---

### Post by geogur on 2009-08-29
update manager is wacky it shows up every day and will not update ? it says / disc is full sugests sudo apt-get clean / but when i do this the manager still says disc full?

---

### Post by running_rabbit07 on 2009-08-29
> **geogur said:**
> update manager is wacky it shows up every day and will not update ? it says / disc is full sugests sudo apt-get clean / but when i do this the manager still says disc full?

What are your system specs?

Are you using Wubi or dual boot?

How big are your partitions?

---

### Post by sahabcse on 2009-08-29
Hi

Paste the o/p of

#df -h

---

### Post by prshah on 2009-08-29
> **geogur said:**
> update manager is wacky it shows up every day and will not update ? it says / disc is full sugests sudo apt-get clean / but when i do this the manager still says disc full?

"sudo apt-get clean" will free up space on your hard drive by deleting .deb installer files that are no longer required. It will not install a program called "clean" to your system.

You can run it even in a HDD full situation.

If you are not able to boot into the regular GUI, you can use the recovery console from the grub menu to perform the same command.

Or, you can simply```
sudo rm -rf /var/cache/apt/archives/
``` to do a similar action. (but apt-get clean is recommended).

---

### Post by geogur on 2009-09-18
fixed my problem i had too many installs on my pc so when i did a fresh install of ubuntu 9.04 on the entire disk . i did not realise i was installing along side  not over righting the old installs . so every time i would reinstal i made matters worse . but its all good now i can make this one as solved

---


---
title: "i need a way to delete all files"
date: 2009-07-18
forum: General Help
---

### Post by tkstvmn on 2009-07-18
and restore my ubuntu installation to be exactly like i just installed it. is there a way to do this?

---

### Post by t4thfavor on 2009-07-18
look up the usage information of a program called tar, it can help you ad all the files to a compressed archive, and copy them to a disk. There are plenty of tutorials available for backing up a Linux workstation.

---

### Post by mgranet on 2009-07-18
There's really not a fast way that I'm aware of. If you were really set on doing that, you could go through your package manager and delete everything you remember installing, then running ```
sudo apt-get autoclean
``` and ```
sudo apt-get autoremove
```.

Or, you could just re-install. Would be faster and easier.

---

### Post by DeMus on 2009-07-18
> **tkstvmn said:**
> and restore my ubuntu installation to be exactly like i just installed it. is there a way to do this?

When you erase all files how do you plan to restore Ubuntu in a way you had it before? You will need to re-install. During install make sure to use the whole disk and choose to format the disks. This way all things from the install you have now will be gone.

---


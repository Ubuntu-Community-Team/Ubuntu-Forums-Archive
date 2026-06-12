---
title: "Undoing a 2-distro dual boot"
date: 2011-10-17
forum: General Help
---

### Post by Forte125 on 2011-10-17
Currently I have Elementary OS and Ubuntu 11.10 in a dual boot.  If I want to remove Elementary can I just delete the partition?

---

### Post by dcstar on 2011-10-17
> **Forte125 said:**
> Currently I have Elementary OS and Ubuntu 11.10 in a dual boot.  If I want to remove Elementary can I just delete the partition?

Remove it using **gparted**, then:

```
sudo dpkg-reconfigure grub-pc
```

And make sure the Grub boot loader is installed on your hard disk.

---


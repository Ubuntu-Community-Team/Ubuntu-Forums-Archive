---
title: "Reinstalling but keeping my /home partition..."
date: 2010-03-15
forum: General Help
---

### Post by jblaven on 2010-03-15
OK,

I have a /home partition at /dev/sda3 and I am currently in Gparted.  I wanted to know if I am supposed to re-identify it somehow when I re-install ubuntu on /dev/sda2.

It seems to me that it would try and create a new home directory on /dev/sda2 unless I tell it otherwise.  Is this correct?  I just want to make sure I **don't** do two things...

1. End up with 2 home directories
2. Delete my existing home directory at /dev/sda3 (with my files) :shock:

Looks like I need some hand holding :mrgreen:.  Any help is greatly appreciated!

Joe

---

### Post by prodigy_ on 2010-03-15
> **jblaven said:**
> It seems to me that it would try and create a new home directory on /dev/sda2
If you're unsure, better just leave /dev/sda3 alone. This way you'll keep your files in any case. When the installation will complete, empty your newly created home directory and edit /etc/fstab to make /home the new mount point for /dev/sda3 and reboot.

---

### Post by howefield on 2010-03-15
After selecting manual partitioning during the install process,  mount /home in the normal way, but ensure that it is not marked for formatting.

Back up your files before installing, good practice in normal circumstances never mind a reinstall.

---

### Post by jblaven on 2010-03-15
> **howefield said:**
> After selecting manual partitioning during the install process,  mount /home in the normal way, but ensure that it is not marked for formatting.

Back up your files before installing, good practice in normal circumstances never mind a reinstall.


Thanks guys,

Worked like a charm!

Joe

---


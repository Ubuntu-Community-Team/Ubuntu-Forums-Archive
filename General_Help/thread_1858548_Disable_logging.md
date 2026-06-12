---
title: "Disable logging"
date: 2011-10-12
forum: General Help
---

### Post by Dronga on 2011-10-12
My Ubuntu is 11.04
I also add in /etc/fstab next text:
> tmpfs      /var/log/apt    tmpfs        defaults           0    0
tmpfs      /var/log         tmpfs        defaults           0    0
tmpfs      /tmp             tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0but after reboot all those directories are not empty.

---

### Post by ajgreeny on 2011-10-12
> **Dronga said:**
> My Ubuntu is 11.04
I also add in /etc/fstab next text:
but after reboot all those directories are not empty.
No, they won't be.

This happens, I think, as during the boot process a lot of logs and files are written and go into /tmp or /var/log, wherever it happens to be.

Or have I misunderstood what you are trying to do here.

---


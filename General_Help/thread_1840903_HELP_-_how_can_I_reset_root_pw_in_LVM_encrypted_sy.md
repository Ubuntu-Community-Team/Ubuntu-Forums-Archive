---
title: "HELP - how can I reset root pw in LVM encrypted system?"
date: 2011-09-08
forum: General Help
---

### Post by vcrpcant on 2011-09-08
How can I reset root password in a LVM encrypted system? :(

I have the LUKS password, but unfortunately can't remember the user and root ones :(

Any help would be very appreciated!

---

### Post by Zeta-K on 2011-09-08
boot a rescue cd (like knoppix) and enter the following commands (replacing things in {}s with what they say):
```
# mkdir /mnt/root
# mount -t ext3 {your partition, probably /dev/sda1, /dev/sda2, /dev/sdb1, or /dev/sdb2} /mnt/root
# chroot /mnt/root /bin/bash
# passwd root
# {password you want}
# {password you want again}
```remember the #'s mean new line

_**EDIT:**_ Never mind, I didn't read LVM encrypted in your question. This advice is useless.

---

### Post by Beacon11 on 2011-09-08
FYI, your question may very well violate the forum Code of Conduct: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) .

---

### Post by Zeta-K on 2011-09-08
> **Beacon11 said:**
> FYI, your question may very well violate the forum Code of Conduct: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) .
 
Why?

---

### Post by vcrpcant on 2011-09-08
> **Beacon11 said:**
> FYI, your question may very well violate the forum Code of Conduct: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) .

Why?? :confused:

---

### Post by vcrpcant on 2011-09-09
bump...

---


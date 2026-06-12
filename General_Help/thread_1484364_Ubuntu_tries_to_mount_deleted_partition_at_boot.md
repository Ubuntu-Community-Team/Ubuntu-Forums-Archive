---
title: "Ubuntu tries to mount deleted partition at boot"
date: 2010-05-15
forum: General Help
---

### Post by bep7987 on 2010-05-15
I deleted a Windows 7 release candidate partition from my computer. Now when I boot into ubuntu, it still tries to mount the deleted partition and I have to hit the letter 's' to skip mounting the partition each time my system boots.

Where is ubuntu getting this partition information from and what can I do to remove it?

Thank you.

---

### Post by oldfred on 2010-05-15
Did you at some time add it to /etc/fstab?

gksudo gedit /etc/fstab

compare to
sudo blkid

and see if any UUIDs not in blkid are in fstab.

---

### Post by bep7987 on 2010-05-15
No, I didn't add it to fstab--not manually, at least.

---

### Post by bep7987 on 2010-05-15
Yes, it is listed in fstab but not when I run blkid.

---

### Post by bep7987 on 2010-05-15
I backed up the fstab file.
```
sudo cp /etc/fstab /etc/fstab.bak
```and then edited the fstab
```
gksu gedit /etc/fstab
```and commented out the drive in question by putting a # at the beginning of the line.

That eliminated the problem. Thank you for pointing me in the right direction.

---


---
title: "Apparently my disk is full"
date: 2009-08-24
forum: General Help
---

### Post by arandomkiwi on 2009-08-24
Apparently my disk is full (its says so as an error when try to edit a file) Its not. It has 312 gb left. This means I can't save any files. How can I save files/get rid of this bug?

---

### Post by anaconda on 2009-08-24
Do you have a separate /root partition?
Maybe that is full.

type
```
df -h

```
in terminal, and you should see how much space you have in all your partitions.

If one of them is full try to make more room by eg. emptying the trash, and apt-cache

If your root partition is full, then root users Trash and apt-cache are probably the reason.

---

### Post by wojox on 2009-08-24
You could have a look at this thread as well:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by prshah on 2009-08-24
> **arandomkiwi said:**
> Apparently my disk is full
Its not. It has 312 gb left.

Can you post the output of the following terminal (Applications-Accessories-Terminal) commands for more information```
df -i
sudo fdisk -l
cat /etc/fstab

```

---


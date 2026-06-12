---
title: "assign swap"
date: 2010-01-11
forum: General Help
---

### Post by jwxie on 2010-01-11
Is it possible to assign a particular swap to an existing environment?

I have two swaps available for some reasons.

---

### Post by michy99 on 2010-01-11
The swap partition is mounted at boot if it is listed in /etc/fstab, so you can change that line if you want to use a different swap partition. You can probably get rid of the unused one. If you post the output of```
sudo fdisk -l
cat /etc/fstab
```then we can get a better idea of your situation.

---


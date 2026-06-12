---
title: "partition doesn't mount."
date: 2010-04-01
forum: General Help
---

### Post by arturus on 2010-04-01
Hello. I have strange problem with my partition. I made automount my partition and everything was ok, but today it doesn't mount. I tried change my /etc/fstab but nothing works(/dev/sda5 or UUID). When I deleted line with automounting i could see my partition in menu/places. Could you tell me where the problem is? Or link to similar topic, because I don't know what I should search.

Thx in advance.

---

### Post by arturus on 2010-04-01
Hm, and it works again. I deleted "#data" and tabulators in /etc/fstab. I don't understand it. Can somebody explain me it?:)

---

### Post by Morbius1 on 2010-04-01
Why not post the output of the following commands so people can see what's going on:

**sudo blkid -c /dev/null**
**cat /etc/fstab**

---


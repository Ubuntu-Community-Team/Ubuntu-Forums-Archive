---
title: "chkdisk on media card"
date: 2009-09-24
forum: General Help
---

### Post by jrmontg on 2009-09-24
my blackberry is saying that I need to run chkdisk on my Micro Secure Digital media card. How can I do this with Ubuntu?

Why do they assume we have windows?

---

### Post by dcstar on 2009-09-25
> **jrmontg said:**
> my blackberry is saying that I need to run chkdisk on my Micro Secure Digital media card. How can I do this with Ubuntu?



```
umount /dev/whatever
sudo fsck /dev/whatever
```

---


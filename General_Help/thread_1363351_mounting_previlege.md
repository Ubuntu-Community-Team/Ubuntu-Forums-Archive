---
title: "mounting previlege"
date: 2009-12-24
forum: General Help
---

### Post by wirate on 2009-12-24
I can mount one of my partitions by:
```

sudo mount /dev/sdax /media/xxx

```

but not by simply clicking the places entry. It says "you are not previleged to mount this volume" neither does ntfs configuration tool detect it.

Thanks

---

### Post by wirate on 2009-12-25
bumpy bump

---

### Post by Morbius1 on 2009-12-25
Could you post the output of these three commands please:

Open **Terminal**
Type **cat /etc/fstab**
Type **sudo blkid**
Type **mount**

And can you point out which of the sdax partitions is the one you want to mount?

---

### Post by wirate on 2009-12-27
Sorry I could not follow up.

I did a clean install to upgrade and the problem does not exist anymore :guitar:

---


---
title: "cryptsetup"
date: 2010-03-25
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2010-03-25
So I'm so close to an error free system I can taste it. The last one that comes up in my playing is ```
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda5
                     UUID=4d8c2aa0-6841-4464-a295-f152a4ebae8b
```

So google helped a bit as there were search results related to the matter but when I looked at /etc/initramfs-tools/conf.d/resume I see that the UUID for swap is right. Also right in fstab. I have no idea where else it would be looking at. I have never been able to hibernate and it would be nice to.

---

### Post by darolu on 2010-03-25
Is your swap encrypted?

---

### Post by Sin@Sin-Sacrifice on 2010-03-25
I don't believe so unless the home encryption does swap as well. I honestly haven't looked into ubuntu's encryption all that much.

---


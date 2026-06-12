---
title: "How to install grub2 on another disk?"
date: 2010-12-29
forum: General Help
---

### Post by spoon_ on 2010-12-29
Here's my situation: I have Ubuntu installed on disk1, but grub2 is installed on disk2. I'd like to get rid of disk2 (it's old), but when I take it out, I can't boot Ubuntu. Does someone know how I can get grub2 onto disk1 so I can get rid of disk2?

Thanks!

---

### Post by spoon_ on 2010-12-29
Ah, so simple:
```

sudo grub-install /dev/sdb

```

---


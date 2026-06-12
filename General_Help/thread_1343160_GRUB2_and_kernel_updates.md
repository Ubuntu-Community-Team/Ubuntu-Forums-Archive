---
title: "GRUB2 and kernel updates"
date: 2009-12-01
forum: General Help
---

### Post by PgR on 2009-12-01
Hi all,

My boot partitions are raided (/boot is /dev/md0)

Back in 9.04 when I had a kernel update I had to run ```
grub
root (hd0,0)
setup (hd0)
root(hd1,0)
setup (hd1)
```
to ensure it would boot from either disk if one died.

Now with grub2 in 9.10 I don't have the grub command...

So do I need to do anything when I get a kernel update? Will it "just work"?

---


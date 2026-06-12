---
title: "symlinks less efficient when linked to symlinks?"
date: 2011-04-17
forum: General Help
---

### Post by UncleBoarder on 2011-04-17
Given...

**ln -s /mnt/data0 /data1**

I assume this...
[B]
ln -s /mnt/data0 /data2[/B]

Is more efficent that this...
[B]
ln -s /data1 /data2[/B]

And therefore I should not use the second method?

---

### Post by marshmallow1304 on 2011-04-18
Technically yes, but the performance hit would be *very* minimal in this example.

---


---
title: "Massive Memory Loss after atempt to compile kernel"
date: 2009-10-19
forum: General Help
---

### Post by [Rolamoto] on 2009-10-19
I tried to compile the latest Linux kernel using [these]("http://ubuntuforums.org/showthread.php?t=442941") instructions. Before I started I had about 10GB on my system, but after I only had about 750MB left. Is there any way to get the disc space back?

---

### Post by Giblet5 on 2009-10-19
> **'[Rolamoto] said:**
> I tried to compile the latest Linux kernel using [these]("http://ubuntuforums.org/showthread.php?t=442941") instructions. Before I started I had about 10GB on my system, but after I only had about 750MB left. Is there any way to get the disc space back?

Bring up a terminal.

Change to the top directory of the linux source.

```
make clean
```

That will wipe out the compiled code, leaving the source.

In other news: if you only have 10G free, that's not a good time to install and build a kernel.

Furthermore, if you have less than 10% free, you will take a massive performance hit on writes.

---

### Post by [Rolamoto] on 2009-10-19
Thanks, that fixed it,

---


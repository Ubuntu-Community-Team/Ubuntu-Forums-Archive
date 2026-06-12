---
title: "FATAL: Module ext2 not found"
date: 2006-01-24
forum: General Help
---

### Post by hk_2999 on 2006-01-24
In booting Breezy, the kernel says.

FATAL: Module ext2 not found

But it continued to boot, like nothing happened, and everything is in place happily, anybody know what's wrong in this syste?

---

### Post by nkhansen on 2006-01-24
Sounds weird. Is it a custom kernel, or the default? If it is a default kernel, try reinstalling it through the Package Manager.

---

### Post by smaller on 2006-01-24
I suspect it is a custom kernel. I have this errormessage too on one of my installations. (64bit with smp enabled) It doesn't seem to do much harm though, oddly enough everything is working fine once you're booted, even the ext2 partitions.

---

### Post by slux on 2006-01-24
In that case I suspect the kernel simply has ext2 compiled in instead of a module and some script that wants to load the ext2 modules fails because of that. Nothing serious at all.

---

### Post by Megatog615 on 2006-04-15
I currently have this problem, and have been looking endlessly for how to fix this problem. 

I restart often, so it is a big problem for me.

---


---
title: "Quickly create large file without filling it with zeros?"
date: 2011-07-05
forum: General Help
---

### Post by Interruptor on 2011-07-05
Every tutorial about swap file creation is using ```
dd if=/dev/zero
```
But is there any faster method: just to mark this region on disk belonging to a file without writing to it?
Something in ext4 tools?

---

### Post by dcstar on 2011-07-06
> **Interruptor said:**
> Every tutorial about swap file creation is using ```
dd if=/dev/zero
```
But is there any faster method: just to mark this region on disk belonging to a file without writing to it?
Something in ext4 tools?

```
man fallocate
```

---

### Post by Interruptor on 2011-07-06
Great, thanks a lot =)

---


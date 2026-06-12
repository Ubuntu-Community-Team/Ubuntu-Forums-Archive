---
title: "&quot;Errors were found while checking the disk for /&quot;"
date: 2011-12-01
forum: General Help
---

### Post by a_p3rson on 2011-12-01
When I boot (I use a dual-boot system if it matters), and I hit the plymouth splash screen, I always get a message saying "Errors were found while checking the disk for /" message, asking to fix, ignore, skip or recover. Ignoring works fine, although I can't push "i" when I am out of the room. Any fixes?

The full fstab line for that drive is
```
UUID=9e0e836c-d89c-46c3-b95f-f5f58a7d3be9    /    ext4    errors=remount-ro    0    1
```

---

### Post by Rubi1200 on 2011-12-02
Hi,
please post the results of the boot info script so we can get a better overview of the situation.

There is a link at the bottom of my post with instructions.

---

### Post by jocko on 2011-12-02
> **a_p3rson said:**
> When I boot (I use a dual-boot system if it matters), and I hit the plymouth splash screen, I always get a message saying "Errors were found while checking the disk for /" message, asking to fix, ignore, skip or recover. Ignoring works fine, although I can't push "i" when I am out of the room. Any fixes?

The full fstab line for that drive is
```
UUID=9e0e836c-d89c-46c3-b95f-f5f58a7d3be9    /    ext4    errors=remount-ro    0    1
```
Why don't you let it fix the problem instead?

---


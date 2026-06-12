---
title: "&quot;Kernel panic&quot;, can't boot"
date: 2012-03-13
forum: General Help
---

### Post by kurja on 2012-03-13
Another day, another problem =) I power on the computer, all I get is this message: ```
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)
```

Booting from the live cd, the hard drive appears to work as usual, I can access the files and fsck comes clean. What about that swap and extended partitions that ubuntu made during install, I can't fsck them, can I?

By the way this happened immediately after I had tried the 12.04 beta from a live cd.

Help?

---

### Post by linoseros on 2012-03-13
do you have any other kernel version installed so that you can boot on it ?

---

### Post by kurja on 2012-03-13
> **linoseros said:**
> do you have any other kernel version installed so that you can boot on it ?

Yes, doing it now. Seems to boot up fine with an older kernel version.

---

### Post by kurja on 2012-03-13
so... what might I do to fix this?

---

### Post by Gremlinzzz on 2012-03-13
You installed 12.04 beta  and its giving you problems?

A "public Beta" is nothing more than the incomplete Beta software released to the public for further testing. Feedback from real-world usage is often very valuable for identifying problems that need to be resolved before the product is finally released.

---

### Post by kurja on 2012-03-13
> **Gremlinzzz said:**
> You installed 12.04 beta  and its giving you problems?

A "public Beta" is nothing more than the incomplete Beta software released to the public for further testing. Feedback from real-world usage is often very valuable for identifying problems that need to be resolved before the product is finally released.

No, I tried it out off the live cd but did not install. I know it's not supposed (?) to change anything on the hard drive, but thought to mention doing so since that was the last thing I did before getting this problem.

---

### Post by kurja on 2012-03-14
I edited etc/default/grub to default to an older kernel, so now the machine starts up, but with an old kernel version - so it's like avoiding the problem instead of fixing it. Any ideas on what's causing the problem, and how to fix it?

---


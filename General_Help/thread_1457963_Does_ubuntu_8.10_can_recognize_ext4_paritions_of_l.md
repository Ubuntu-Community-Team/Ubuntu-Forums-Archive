---
title: "Does ubuntu 8.10 can recognize ext4 paritions of lucid?"
date: 2010-04-19
forum: General Help
---

### Post by aviramof on 2010-04-19
i have a friend with Ubuntu 8.10 and he doesn't know weather to use ext3 or ext4 if he would install lucid in a separate partition because the ubuntu 8.10 might not recognize the
ext4 partition.

what do you think?

thanks in advance.

---

### Post by klemes on 2010-04-19
I am not sure if ext4 was introduced in 9.04 or 9.10 (I think it was 9.10),but I am pretty sure 8.10 won't recognise any ext4 partitions although it will certainly see jfs and xfs partitions amongst others.

---

### Post by oldos2er on 2010-04-19
> **aviramof said:**
> i have a friend with Ubuntu 8.10 and he doesn't know weather to use ext3 or ext4 if he would install lucid in a separate partition because the ubuntu 8.10 might not recognize the
ext4 partition.

what do you think?


Unless you go out of your way to compile a new kernel for 8.10, I don't think it's going to recognize an ext4 partition (ext4 support didn't come around until 9.04).

If your friend allows Lucid to install its grub2, instead of keeping legacy grub, file system type won't matter.

---


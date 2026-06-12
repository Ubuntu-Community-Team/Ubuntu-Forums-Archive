---
title: "Bad Superblock"
date: 2011-11-27
forum: General Help
---

### Post by Shvesley on 2011-11-27
Can't mount sda1 or boot to it. So I tried this from my live usb...
$ sudo e2fsck -f -b 32768 -y /dev/sdb1
It did some stuff and had crazy matrix code and it is now just repeating "y"

What is going on?

---

### Post by Shvesley on 2011-11-29
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

I just followed this article.

---

### Post by Geekylad on 2011-12-01
> **Shvesley said:**
> [http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

I just followed this article.

I followed that article too, but to no avail. None of the backup superblocks worked.

I still have a non-bootable system, any suggestions?

---

### Post by Shvesley on 2011-12-27
All I can say is try the instructions again. Be sure to wait for a while it will eventually sort things out.

---


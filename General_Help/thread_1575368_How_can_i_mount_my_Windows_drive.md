---
title: "How can i mount my Windows drive?"
date: 2010-09-15
forum: General Help
---

### Post by mrhank on 2010-09-15
Hi fellas, I hope my question isn't too noobish. I'm new to linux so please bare with me. I installed Ubuntu 10.04 and I love it. the only problem I'm having is that I can't seem to mount my windows drive in order to see my files(music, pics, vids). how can i do this? I have 4 500gb disks and i can only see two of them and neither one is my windows drive. Any help is greatly appreciate it.
thnx

Windows 7/ubuntu 10.04 installed using wubi

---

### Post by bcbc on 2010-09-15
The partition you installed wubi on is mounted under /host (Places, Computer, File system, host).

Not sure why a second partition would not be visible. Run 'sudo blkid' from the terminal (CTRL+ALT+t) and see what file system it identifies on the partition.

---

### Post by mrhank on 2010-09-15
Duuuude thank you so much. It was that simple. Sorry for my newbie question. Now I can use Ubuntu full time. Thx a lot man! :) :) :)

---

### Post by bcbc on 2010-09-15
No prob :)

It's not a newbie question... it's hardly intuitive.

---

### Post by WorMzy on 2010-09-15
Be aware that Ubuntu isn't designed to be run in Wubi. For best performance, install Ubuntu to a partition, I'd guess that you have more than enough space for it.

You should only really use Wubi for trying out Ubuntu, so be careful what updates you install, and don't try to upgrade to 10.10 when it gets released next month - you may end up with an borked Ubuntu installation.

---

### Post by bcbc on 2010-09-15
> **WorMzy said:**
> Be aware that Ubuntu isn't designed to be run in Wubi. For best performance, install Ubuntu to a partition, I'd guess that you have more than enough space for it.

You should only really use Wubi for trying out Ubuntu, so be careful what updates you install, and don't try to upgrade to 10.10 when it gets released next month - you may end up with an borked Ubuntu installation.

Also if you install directly to partition, be vewy vewy careful.

---


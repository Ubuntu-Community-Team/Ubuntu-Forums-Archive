---
title: "how to write to a fat32 drive?"
date: 2004-10-22
forum: General Help
---

### Post by Vulc on 2004-10-22
I know my code is wrong since I can only read off it, what options should I be using?

/dev/hdb5       /mnt/shared     vfat    rw,umask=000    0       0

---

### Post by sfw5000 on 2004-10-22
I was just doing this like

mount -t vfat /dev/hdb5 /mnt/shared

then just set the permisions to be writable (chmod 777 /mnt/shared)

And that was it. 

HTH

Sam

---

### Post by Vulc on 2004-10-23
woot that worked thanks =)

---


---
title: "Adding new linux image"
date: 2010-02-17
forum: General Help
---

### Post by viniciuscarvalho on 2010-02-17
Hello there! I was using linux image 2.6.31-16 and today I've updated to 2.6.31-19. But on the grub menu lst menu I chose keep current, and my menu.lst does not point to the new image.

Looking at the file is easy to add the new entry, but I wonder how do I find/generate the uuid for the image:

title          Ubuntu 9.10, kernel 2.6.31-16-generic
uuid           9d2d3afc-1efa-4f08-b9e6-088f93238dd2
kernel         /boot/vmlinuz-2.6.31-16-generic root=UUID=9d2d3afc-1efa-4f08-b9$
initrd         /boot/initrd.img-2.6.31-16-generic


Regards

---

### Post by zvacet on 2010-02-17
Try 

```
sudo update-grub
```

---

### Post by louieb on 2010-02-17
UUID is how Ubuntu identifies a partition. 

Use the same one. -

---

### Post by viniciuscarvalho on 2010-02-17
Thanks :)

---


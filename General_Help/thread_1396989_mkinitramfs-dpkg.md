---
title: "mkinitramfs-dpkg"
date: 2010-02-02
forum: General Help
---

### Post by veda87 on 2010-02-02
I have a problem with mkinitramfs-dpkg.

When I used it to create the ramdisk image, it is creating initrd.img-2.6.32.7-custom of size 10 times more than the normal one..
```
-rw-r--r-- 1 root root  7645224 2010-02-01 22:29 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root  7648659 2010-02-01 23:03 initrd.img-2.6.31-17-generic
-rw-r--r-- 1 root root 70061921 2010-02-02 18:14 initrd.img-2.6.32.7-custom

```

while running mkinitramfs-dpkg, it gives me some warning like this
```
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32.7-custom-10.00.Custom was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32.7-custom-10.00.Custom was configured last, according to dpkg)
Running postinst hook script update-grub.

```

Can anyone tell me what problem is this and how to solve it...

---


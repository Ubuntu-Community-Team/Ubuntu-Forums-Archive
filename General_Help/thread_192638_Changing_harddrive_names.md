---
title: "Changing harddrive names"
date: 2006-06-09
forum: General Help
---

### Post by Ubuntuud on 2006-06-09
Hi,
I recently reformatted my external HDD, but now the partitions have names like "usbdisk" and _PNG<001A>. How can I change this? Thanks in advance!

---

### Post by scxtt on 2006-06-09
if you're just plugging it in, via USB, it'll auto mount it and assign it whatever name it wants (there might be a config file on the drive itself for setting that) ...

you should be able to specify how you want it to mount in /etc/fstab ... check out your fstab and try creating an entry for it ...

---


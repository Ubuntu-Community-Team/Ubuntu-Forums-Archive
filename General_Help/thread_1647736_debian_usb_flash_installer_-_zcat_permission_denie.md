---
title: "debian usb flash installer - zcat: permission denied"
date: 2010-12-17
forum: General Help
---

### Post by jim78 on 2010-12-17
I'm trying to prepare a usb flash disk to create a debian boot disk. I run this command and get permission denied:

zcat boot.img.gz > /dev/sde

Same if i run it with sudo. Can anyone tell me why???

Cheers,

James.

---

### Post by debox1 on 2011-02-03
I was having exactly the same issue but I just solved it....

Just type

chmod 666 /dev/sde

which is going to change permissions for the usb flash drive and now you would be able to use "zcat" command....

Hope still helps

Luis

---


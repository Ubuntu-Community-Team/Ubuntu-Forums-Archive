---
title: "Encrypting the hard disk and bootloader"
date: 2012-08-25
forum: General Help
---

### Post by void00 on 2012-08-25
I would like to encrypt the entire hard disk and also the grub boot loader and authenticate the access with a password. From the threads I've read, one way I found out was to start over fresh using the lvm file system (I don't know if I understood it right).

But, I've a lot of data/programs currently present/installed and it will be a pain to backup and copy back and such. 

I would like to know if there's any other alternative way by which I could avoid installing a fresh copy of Ubuntu. It'd be really helpful if you could point out some way.

My system dual boots Ubuntu 12.04 and Windows 7.
Thanks.

---

### Post by Laiquendi on 2012-08-25
TrueCrypt should be able to do it, alas I'm not sure. But it's my best shot :P

---

### Post by void00 on 2012-08-25
> **Laiquendi said:**
> TrueCrypt should be able to do it, alas I'm not sure. But it's my best shot :P

Yes I've seen TrueCrypt, but the Ubuntu version doesn't support encrypting the bootloader and I don't think the windows version recognizes the ext3 partition.
Thanks for the reply! :)

---

### Post by Megaptera on 2012-08-25
"This is an installation guide for Ubuntu Desktop 12.04 LTS that will show you how to enable full disk encryption ..." [http://rationallyparanoid.com/articles/ubuntu-12-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-12-lts-security.html)

---

### Post by void00 on 2012-08-25
> **Megaptera said:**
> "This is an installation guide for Ubuntu Desktop 12.04 LTS that will show you how to enable full disk encryption ..." [http://rationallyparanoid.com/articles/ubuntu-12-lts-security.html](http://rationallyparanoid.com/articles/ubuntu-12-lts-security.html)

Thanks, but this requires me to start over with a new ubuntu installation using the alternate download. I was hoping to find if there's any way to do this with the current installed os.

---

### Post by Laiquendi on 2012-09-05
Try to bootup with TrueCrypt, I've seen this with Unebootin I think.

---


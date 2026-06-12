---
title: "Ubuntu - XUbuntu : USB mounting difference"
date: 2010-02-08
forum: General Help
---

### Post by Rob8900 on 2010-02-08
Hi,

When I copy a file to my USB stick on **Ubuntu**, the data is **immediately **written to the stick. 

When I copy a file to my USB stick on **XUbuntu**, the data is written to stick **after about 30 seconds**.

How can I enable the immediate writing to the USB stick in XUbuntu?


Thx,

Rob

---

### Post by HPD2 on 2010-02-08
Are you using the same hardware for both Ubuntu and Xubuntu? If not it could be a limitation of the hardware rather than the operating system.

---

### Post by Grenage on 2010-02-08
I believe if you add an fstab entry and use the *sync* option, it will write the data immediately (synchronously rather than asynchronously).

---

### Post by Rob8900 on 2010-02-08
> **HPD2 said:**
> Are you using the same hardware for both Ubuntu and Xubuntu? If not it could be a limitation of the hardware rather than the operating system.

No, it's not the same hardware I try on. I will try this too.

---

### Post by 3rdalbum on 2010-02-08
It would be a better idea to do the opposite - write data out to the device after a delay, rather than immediately. The delay causes fewer writes*, which in turn increases the life of the flash memory. You also get a quicker write speed too, actually.

*Let's say you create a file on your flash drive - it's a letter to your mother. You write the letter and then save it. Then you realise you misspelt a word and you change it and save it again. Without the delay, the flash will be written to twice. With the delay, the flash will be written to once.

---


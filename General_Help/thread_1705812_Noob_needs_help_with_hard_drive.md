---
title: "Noob needs help with hard drive"
date: 2011-03-12
forum: General Help
---

### Post by n3k01 on 2011-03-12
Hi i have used ubuntu before but never as a primary OS, now i got a new Netbook and i wanted to install the Ubuntu Netbook edition, the problem comes after i installed it and is that i cannot access the secondary partition, i had already placed several files on it (around 20GB) and i dont know how to access it. i dont have access to my backup of that info at the moment so formatting it is not an option, the partition y in NTFS. XD



found it thanks

---

### Post by Hedgehog1 on 2011-03-12
n3k01,

We need to get a look at your disk partition layout so we can help you find that partition.

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by n3k01 on 2011-03-12
delete

---


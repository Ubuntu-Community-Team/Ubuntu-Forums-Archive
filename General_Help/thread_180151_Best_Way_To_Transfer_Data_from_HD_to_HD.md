---
title: "Best Way To Transfer Data from HD to HD"
date: 2006-05-21
forum: General Help
---

### Post by eyebrowman92 on 2006-05-21
I just purchased a brand new 120GB hd, and was wondering if anyone knows the best way I can transfer all my data from the old one to the new one. Any ideas?

---

### Post by Ramses de Norre on 2006-05-21
```
sudo -i
cd /
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newdisk
```
When you've mounted the hard disk at /mnt/newdisk and want to transfer everything under / to it.

---

### Post by eyebrowman92 on 2006-05-21
[QUOTE=Ramses de Norre]```
sudo -i
cd /
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newdisk
```
When you've mounted the hard disk at /mnt/newdisk and want to transfer everything under / to it.[/QUOTE]

I'd just like to transfer my /home dir. Would i just cd to the /home dir?

---

### Post by Ramses de Norre on 2006-05-21
Yes, indeed. And don't use the sudo -i then, it will mess up permissions on the new home folder.

---

### Post by eyebrowman92 on 2006-05-21
[QUOTE=Ramses de Norre]Yes, indeed. And don't use the sudo -i then, it will mess up permissions on the new home folder.[/QUOTE]

Ok Thanks.

---

### Post by eyebrowman92 on 2006-05-21
Ok, This is harder than I thought.  I've got the black end of the Primary IDE cable plugged into the 120GB HD, and the gray end plugged into the old HD.  Did I do this right?  Also, i've got a bunch of volumes in my Computer location in nautilus. Here's a screenshot:

[http://img79.imageshack.us/my.php?image=screenshot2tp.png](http://img79.imageshack.us/my.php?image=screenshot2tp.png)

Note that I'm using the latest Dapper packages on the new 120GB HD.  Should I copy stuff from the old HD this way, or do it from the old HD?

Please Help!

---


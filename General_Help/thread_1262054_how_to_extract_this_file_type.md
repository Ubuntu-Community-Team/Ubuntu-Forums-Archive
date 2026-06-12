---
title: "how to extract this file type?"
date: 2009-09-09
forum: General Help
---

### Post by abhilashm86 on 2009-09-09
i got a mail in this type, not able to extract?
```
abhilash@abhilash:~/Desktop$ ls -l letters.7z
-rw-r--r-- 1 abhilash abhilash 430639 2009-09-09 22:21 letters.7z

```
please tell how to do it.......

---

### Post by briantoumbs on 2009-09-09
.7z is 7 zip
Think you can just right click and extract or 

Linux uses p7zip to extract 7zip files.

sudo apt-get install p7zip

p7zip -d filename.7z

---

### Post by mjitkop on 2009-09-09
Hi, abhilashm86.

You need to install the 7-Zip package in Applications -> Add/Remove.

Once this is done, right click on the file and extract using 7-Zip.

That should work. :)

-------

Oops, briantoumbs was quicker! ;-)

---

### Post by abhilashm86 on 2009-09-09
yea thanks friends:) did extract easily, i donno why ppl will make so many types of archives? makes confusing......

---


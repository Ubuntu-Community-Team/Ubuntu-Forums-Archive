---
title: "Diskless folder permission problems"
date: 2010-09-26
forum: General Help
---

### Post by 2ramiro on 2010-09-26
Hello

I succesfully made a Diskless ubuntu with windows 2003 as server and [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto) this how to, but 
```
cp -ax /. /mnt/.
``` hasn't copied the file permissions and now all folders are 777 
and sudo gives out this error sudo: must be setuid root.
Was it maybe wrong to run 
```
cp -ax /. /mnt/.
``` as sudo ?
This also didn't help:
```
 chown root:root /usr/bin/sudo chmod 4755 /usr/bin/sudo
```.

How can i get sudo back :( ? 
Thank you for your help.

---


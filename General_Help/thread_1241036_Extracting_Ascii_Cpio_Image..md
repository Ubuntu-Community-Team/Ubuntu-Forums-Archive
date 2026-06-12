---
title: "Extracting Ascii Cpio Image."
date: 2009-08-15
forum: General Help
---

### Post by Xqtftqx on 2009-08-15
Hello everybody, 

Ive had this file ive been trying to work with to get it extracted. Arc could view the files inside of it, but couldnt extract any of them.

I ran File then tried to extract it with cpio. Heres the outputs:

```

tyler@tyler-laptop:~/Desktop$ file install.img 
install.img: ASCII cpio archive (SVR4 with no CRC)
tyler@tyler-laptop:~/Desktop$ cpio -iv < install.img
cpio: /swupdate/US02.img.tar: Cannot open: No such file or directory
/swupdate/US02.img.tar
cpio: /swupdate/US02.img.tar.md5: Cannot open: No such file or directory
/swupdate/US02.img.tar.md5
cpio: /swupdate/verindex.txt: Cannot open: No such file or directory
/swupdate/verindex.txt
62222 blocks
tyler@tyler-laptop:~/Desktop$
```

I could also list the inside of the file with this:
```

tyler@tyler-laptop:~/Desktop$ cpio -itv -I distribution.tar.gz 
cpio: Cannot open distribution.tar.gz: No such file or directory
tyler@tyler-laptop:~/Desktop$ cpio -itv -I install.img 
-rwxr-xr-x   1 root     root     31856640 Aug  6 06:50 /swupdate/US02.img.tar
-rwxr-xr-x   1 root     root           33 Aug  6 06:50 /swupdate/US02.img.tar.md5
-rwxr-xr-x   1 root     root          185 Aug  6 06:50 /swupdate/verindex.txt
62222 blocks

```
Now i am completely stuck, any help is appreciated! Thank you so much

---

### Post by michy99 on 2009-08-15
Have you tried mounting the .img?```
sudo mkdir /mnt/install
sudo mount -o loop install.img /mnt/install
```You may have to give the full path to install.img.

---


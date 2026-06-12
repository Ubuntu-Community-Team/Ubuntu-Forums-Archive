---
title: "permsissions not set after issuing chmod command"
date: 2011-06-15
forum: General Help
---

### Post by apoorvmunshi on 2011-06-15
please hav a look at  the image. i hav two users ,one is apoorv(administrator) and other is others(ordinary user). i want to restrict the ordinary user from accessing the files directory as shown in picture. so i tried the chmod command with o-rw option. but its not working ..

NOTE : i hav enabled auto mount for all partitions at boot time

---

### Post by apoorvmunshi on 2011-06-15
the owner of the directory is apoorv!!

---

### Post by ruffEdgz on 2011-06-15
Why don't you make the directory 750?
```

sudo chmod 750 ./files

```
That will change the other permissions for 'files' so rwx isn't there.

Cheers!

---

### Post by Morbius1 on 2011-06-15
This is how you automounted your partition from another thread:
> /dev/sda6 /media/apoorv ntfs-3g auto,uid=1000,gid=1000,umask=002 0 0You cannot chmod or chown an ntfs partition because there are no linux permission or ownership bits to set on an individual file basis. 

If you only want you to have access to this partition then change "umask=002" to "umask=077" or "umask=007":
> /dev/sda6 /media/apoorv ntfs-3g auto,uid=1000,gid=1000,umask=077 0 0 A "0" allows full access - a "7" removes all access.

---

### Post by apoorvmunshi on 2011-06-16
oh thanks a lot!! that waas very helpful!! i just love this forum..there are so many nice ppl to help newbies...:D

---


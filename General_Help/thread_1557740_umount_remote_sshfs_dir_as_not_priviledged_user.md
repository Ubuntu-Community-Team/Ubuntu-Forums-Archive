---
title: "umount remote sshfs dir as not priviledged user"
date: 2010-08-21
forum: General Help
---

### Post by bogaczew on 2010-08-21
I added sshfs to /etc/fstab, set owner and group of local dir, added user to user group, and now:

I can mount remote dir without problem

```
pawel@sigma:~$ ls /media/lambda/dane/
pawel@sigma:~$ mount /media/lambda/dane/ 
pawel@sigma:~$ ls /media/lambda/dane/
filmy  isos  ksi&#261;&#380;ki  muzyka  muzyka2  zdj&#281;cia
pawel@sigma:~$ 
```

but I cannot umount this dir as user, I must do it as root

```
pawel@sigma:~$ umount /media/lambda/dane/ 
umount: /media/lambda/dane is not in the fstab (and you are not root)
pawel@sigma:~$ sudo umount /media/lambda/dane/ 
pawel@sigma:~$
```

I can use as user fusermount -u

```
pawel@sigma:~$ fusermount -u /media/lambda/dane/
pawel@sigma:~$
```

but I'd like to use just umount. What can be wrong?

---


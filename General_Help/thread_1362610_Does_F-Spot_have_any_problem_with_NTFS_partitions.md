---
title: "Does F-Spot have any problem with NTFS partitions?"
date: 2009-12-23
forum: General Help
---

### Post by TheHimself on 2009-12-23
I can't get F-Spot to import images from NTFS partitions even when I run it as root. It has no problem importing from my home folder.

---

### Post by howefield on 2009-12-23
Don't think it has problems with that, just tried it and imported fine.

Is the ntfs partition/disk mounted ?

---

### Post by mikem94590 on 2009-12-23
It seems to work for me.  I use F-Spot at work, and co-workers often hand me NTFS pendrives, and I've always been able to successfully import photos.  If nothing else, you should be able to simply mount the NTFS drive and access the photo files (.jpeg, .png, etc.) from there.

---

### Post by TheHimself on 2009-12-23
When I run it from the command line and then try to import I get the following:

```
System.UriFormatException: URI scheme must start with a letter and must consist of one of alphabet, digits, '+', '-' or '.' character.

``` 

Can it be because the mount point is /media/c:  ?:confused:

---

### Post by howefield on 2009-12-23
> **TheHimself said:**
> Can it be because the mount point is /media/c:  ?:confused:

Hmmm... the error does suggest that might be the problem.

Can you change the mount and try again ?

---

### Post by TheHimself on 2009-12-23
I edited /etc/fstab and now it works. This is a bit weired a problem since other applications like gthumb work fine.

---


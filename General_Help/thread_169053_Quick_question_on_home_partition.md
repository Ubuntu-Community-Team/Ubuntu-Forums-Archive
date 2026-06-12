---
title: "Quick question on /home partition"
date: 2006-05-01
forum: General Help
---

### Post by olsonar on 2006-05-01
i currently have /home on my root partition. I want to change this to another partition I created (5GB, ext3). Can I just copy the contents of the /home direrctory to the new partition and add an entry to /etc/fstab that looks like this:

```
/dev/hda8    /home    ext3    defaults    0    0
```

or is there something else I need to do?

---

### Post by az on 2006-05-01
[QUOTE=olsonar]i currently have /home on my root partition. I want to change this to another partition I created (5GB, ext3). Can I just copy the contents of the /home direrctory to the new partition and add an entry to /etc/fstab that looks like this:
[/QUOTE]
Yup.

You may want to delete the contents of the /home folder before you mount something over it, since you will want to free up the disk space...  The space on your disk will still be used up, otherwise.

---

### Post by aysiu on 2006-05-01
Yes, you can, but how are you going to copy your files? I would advise *tar*ring them (and then untarring them after you've copied the .tar.gz over) instead of just copying them over. Also, don't delete your old /home until you know the new /home partition works.

---

### Post by elamericano on 2006-05-01
That's all folks.

---

### Post by cskeide on 2006-05-01
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---


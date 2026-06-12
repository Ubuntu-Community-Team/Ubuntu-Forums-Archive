---
title: "Cant boot"
date: 2009-11-14
forum: General Help
---

### Post by Sevy on 2009-11-14
Ive accidently changed the permissions for my entire filesystem:oops: and can no longer boot into Jaunty. I recieve the following error-

kinit: No resume image,doing normal boot...
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

After this I have BusyBox v1.10.2 built-in shell with (initramfs) prompt

Is there a way out of this,I dont want to reinstall as I have valuable stuff on my desktop

---

### Post by dabang on 2009-11-14
You mean, you changed permissions on "/"? That's tough... There are not a lot occasions where I'd recommend a reinstall, but this would be one. So, I'd boot with Ubuntu desktop CD, mount partitions, save data and then reinstall.
But wait a little, maybe someone around has a better idea...?

---

### Post by Sevy on 2009-11-14
Yeah Dabang thats all I can think of at the moment,Ill give it a bit of time,maybe a solution

---

### Post by Sevy on 2009-11-14
OK,Ive just booted with the live cd and mounted my partion.
Is there a way of then setting permissions so that everything is accessible?
instead of reinstalling

---

### Post by Monotoko on 2009-11-14
you could use chmod....but they would all have diff file permissions....to get yourself back into a very insecure system, you could type:

```
chmod -R 644 /media/ubuntu
``` (if your partition is mounted there....change it for yours)

---

### Post by Sevy on 2009-11-14
mmm thanks Monotoko,I dont think its worth it if its going to end up insecure,reinstall it is then
:roll:

---

### Post by dabang on 2009-11-15
To make everything accessible, you could either
```

chmod -R 777 /path/to/mounted/ubuntu
```
(with 644 you wouldn't be able to access folders as they need x bit)

-> very insecure, but you can then copy what you need

```
find /path/to/mounted/ubuntu -type d -exec chmod 755 {} \;
find /path/to/mounted/ubuntu -type f -exec chmod 644 {} \;
```

That would also leave everything accessible, but differs between files and folders -> again, only for copying needed stuff, I wouldn't want to a run a system like this...

---


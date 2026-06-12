---
title: "mounting local partition with rw for user"
date: 2010-08-15
forum: General Help
---

### Post by Mia_tech on 2010-08-15
I have a local partition (storage) which is getting mounted, but only su can create folders and files, what's the right options in fstab so users can get rw to the partition?

thanks

---

### Post by deserthowler on 2010-08-15
Look at chmod in the man pages ... go to the terminal and type the following.

```
 man chmod 
```

then you can set permissions as you like.  I can't go any further because I don't know how you want to change permissions.

Earl

---

### Post by Mia_tech on 2010-08-16
> **deserthowler said:**
> Look at chmod in the man pages ... go to the terminal and type the following.

```
 man chmod 
```

then you can set permissions as you like.  I can't go any further because I don't know how you want to change permissions.

Earl

already tried that and set permission for everyone ugo+rwx. I even made myself owner, but still not working

---

### Post by deserthowler on 2010-08-16
Did you run ls -l to see what the output is on that drive?

Earl

---

### Post by Mia_tech on 2010-08-17
> **deserthowler said:**
> Did you run ls -l to see what the output is on that drive?

Earl

yes, I did, but apparently, it didn't take effect; however, I'm showing as the owner, yet I can't create a file

```
brw-rw---- 1 jorge disk 8, 3 2010-08-15 19:55 /dev/sda4
```

---


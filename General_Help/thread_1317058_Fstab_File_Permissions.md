---
title: "Fstab File Permissions?"
date: 2009-11-06
forum: General Help
---

### Post by CrusaderAD on 2009-11-06
I have multiple drive mounted in my fstab file. I can browse the drives just fine, but can't paste anything into the drives. I get this error:

```
Error opening file '/home/user/Network/server1/file.txt': Permission denied
```

I used the exact same syntax in my fstab file for these drives when I was using Jaunty and had no issue. Same user and passwords too. Any ideas?

---

### Post by jollysnowman on 2009-11-06
What permissions are you assigning to the drives?

---

### Post by CrusaderAD on 2009-11-06
Here's what I'm using:

```
//1.1.1.1/server1 /home/user/Network/server1 cifs username=user1,password=pass1 0 0
```

---

### Post by hal10000 on 2009-11-06
Try to set the **rw** option:
```
//1.1.1.1/server1 /home/user/Network/server1 cifs **rw**,username=user1,password=pass1 0 0
```

The manpage of mount.cifs (man mount.cifs) contains detailed info about the optons you can use.

---

### Post by CrusaderAD on 2009-11-06
Thanks for the replies. rw didn't work and man mount.cifs said no manual entry for mount.cifs. I'll have to do some more reseach.

---

### Post by CrusaderAD on 2009-11-06
[http://linux.die.net/man/8/mount.cifs]("http://linux.die.net/man/8/mount.cifs") Had the man page... still looking, read write abilities didn't work when assigning them.

---

### Post by hal10000 on 2009-11-06
> rw didn't work and man mount.cifs said **no manual entry for mount.cifs**. I'll have to do some more reseach.

If you don't have a manual entry for mount.cifs, then i know what your problem is. You don't have the smbfs package installed
```
sudo apt-get install smbfs
```

and everything will be fine.

---


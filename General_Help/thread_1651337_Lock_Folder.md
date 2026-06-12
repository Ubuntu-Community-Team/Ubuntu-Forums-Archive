---
title: "Lock Folder"
date: 2010-12-23
forum: General Help
---

### Post by L Style on 2010-12-23
Is there a software to lock folders. How to lock folders in ubuntu 10.04

---

### Post by Lone_Joker on 2010-12-23
What do you mean by locking a folder? Do you want only one user to be able to see what's inside of a folder?

---

### Post by L Style on 2010-12-23
> **Lone_Joker said:**
> What do you mean by locking a folder? Do you want only one user to be able to see what's inside of a folder?

Yes, locking folder mean. password protect to folder

---

### Post by inkrypted on 2010-12-23
Well I am not sure about locking a folder but there is Truecrypt that can encrypt a virtual drive,partition,or a device and has an option to password protect it.

[http://www.truecrypt.org/](http://www.truecrypt.org/)

Hope it helps.

---

### Post by karthick87 on 2010-12-23
Checkout file permission,

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Lone_Joker on 2010-12-23
> **L Style said:**
> Yes, locking folder mean. password protect to folder

I'm not sure about password protecting, but you can change the permissions on a folder so that only one user can access it. This way you aren't prompted for a password but only one user can access the folder.

Try this
```
# First make sure that you own the folder
chown $user /path/to/folder # you might have to use sudo for this

# Now you can change the permissions so only the owner of the folder can read/write/execute
chmod 700 /path/to/folder
```

NOTE: This will give only the owner of the folder access. If you want to give access to a group of users let me know and I'll try to help you. Also, technically *root* can still access the folder because root has access to *everything* you shouldn't have to worry about this if you haven't tampered with root though.

---


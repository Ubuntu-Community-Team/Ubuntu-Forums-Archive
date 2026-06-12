---
title: "How do I manually generate an entry in the /etc/shadow file?"
date: 2010-10-25
forum: General Help
---

### Post by guest_user on 2010-10-25
I'm trying to learn how to create a user account manually on the system, and I've edited the /etc/passwd and /etc/groups as well as creating a new home directory by copying /etc/skel but I'm stuck at how to generate an entry in the /etc/shadow file since it comprises of the hash and all, any idea how to do it?

---

### Post by SeijiSensei on 2010-10-25
Just use the "adduser" command.  It will create the needed entries in /etc/passwd and /etc/group, create the user's home directory using /etc/skel, and prompt you for the password to create the entry in /etc/shadow.  Type "man adduser" for details.

---

### Post by guest_user on 2010-10-25
> **SeijiSensei said:**
> Just use the "adduser" command.  It will create the needed entries in /etc/passwd and /etc/group, create the user's home directory using /etc/skel, and prompt you for the password to create the entry in /etc/shadow.  Type "man adduser" for details.

I'm trying to learn how to create a user account manually on the system

---

### Post by SeijiSensei on 2010-10-25
Well, OK, but I don't know of anyone who generates the hashes for /etc/shadow manually.  This page looks helpful: [http://joanpuigsanz.wordpress.com/2009/11/26/hack-hash-passwords/](http://joanpuigsanz.wordpress.com/2009/11/26/hack-hash-passwords/).  "man shadow" and "man 3 crypt" might help, too.

The password hashes are generated with SHA1 plus a "salt".  I don't know how the salts are generated; presumably they come from some randomizer.

You could study the source code for adduser and see how it handles it, too.

---

### Post by sisco311 on 2010-10-25
```
man mkpasswd
```

---


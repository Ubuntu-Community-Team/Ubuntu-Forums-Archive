---
title: "privilegies reloaded"
date: 2011-09-12
forum: General Help
---

### Post by Artanis.ro on 2011-09-12
Given the following scenario:

I create a folder, I create a group, I assisgn the folder to that group, also the users and the admin for that group.
I set the rwx privilegies for that group so that only the owner and group could rwx in it.

Is it possible to grant to a user only the permission to add files to that folder? I am asking this because the "w" permissions mean that someone can add files, modifie them and delete them. I don't want someone to erase the other files by mistake. Only to add files, even if the added files are wrong, I will delete them afterwards.


Thank you

---

### Post by matt_symes on 2011-09-12
Hi

> **Artanis.ro said:**
> Given the following scenario:

I create a folder, I create a group, I assisgn the folder to that group, also the users and the admin for that group.
I set the rwx privilegies for that group so that only the owner and group could rwx in it.

Is it possible to grant to a user only the permission to add files to that folder? I am asking this because the "w" permissions mean that someone can add files, modifie them and delete them. I don't want someone to erase the other files by mistake. Only to add files, even if the added files are wrong, I will delete them afterwards.


Thank you

You want user A in a group to be able to add files but ensure that other users in that group (users B,C,D...) cannot delete (or rename, etc) user A files ? User A will still be able to delete (rename, etc) his own files.

If this is the case have a look at the sticky bit. It may help.

From

```
man chmod
```

> RESTRICTED DELETION FLAG OR STICKY BIT
       The  restricted  deletion flag or sticky bit is a single bit, whose interpretation depends on the file type.  For directories, it prevents unprivileged users from removing or renaming a
       file in the directory unless they own the file or the directory; this is called the restricted deletion flag for the directory, and is commonly found on world-writable directories  like
       /tmp.  For regular files on some older systems, the bit saves the program's text image on the swap device so it will load more quickly when run; this is called the sticky bit.

Kind regards

---


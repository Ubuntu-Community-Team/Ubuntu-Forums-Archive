---
title: "groups"
date: 2011-04-05
forum: General Help
---

### Post by kireol on 2011-04-05
I'm trying to add myself to the www-data group but I'm doing something wrong.



```
$ sudo adduser kireol www-data

The user `kireol' is already a member of `www-data'.
$ groups
kireol adm dialout cdrom plugdev lpadmin admin sambashare
```

I tried editing a file owned by www-data with group write and it said it's read only.

---

### Post by sisco311 on 2011-04-05
After adding your (currently logged in) user to a new group you have to start a new login shell (log out and log back in).

---

### Post by kireol on 2011-04-05
worked.  thanks.

---


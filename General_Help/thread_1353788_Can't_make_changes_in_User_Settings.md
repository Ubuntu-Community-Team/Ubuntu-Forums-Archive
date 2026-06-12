---
title: "Can't make changes in User Settings"
date: 2009-12-13
forum: General Help
---

### Post by dannyfel on 2009-12-13
I am using an administrator account but nothing happens when I click on the [Keys Icon] next to "Click to make changes" in the User Settings (System->Administration->Users and Groups). So I can't modify, add or remove users.

By the way, command lines do work (useradd userdel...).

Does anyone know what could be the reason?

Thanks!

---

### Post by Wardje on 2009-12-13
You *don't* get the "Authenticate" window?

---

### Post by dannyfel on 2009-12-13
nope. nothing.

---

### Post by Gerard08 on 2010-01-29
I am having the same problem. I uninstalled and reinstalled gnome-system-tools. No change. 

Went to Configuration editor checked all-users box. no change. Is this a bug?

---

### Post by mickey57 on 2010-02-22
B][SIZE="4"][COLOR="DarkRed"]..9.10-Same Problem here.Can't unlock the damn thing,Never asks' for password..[/COLOR][/SIZE][/B]

---

### Post by Wardje on 2010-02-23
What if you do ALT+F2:
```
gksudo users-admin
```

---


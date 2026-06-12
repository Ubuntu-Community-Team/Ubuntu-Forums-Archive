---
title: "change password for user"
date: 2011-03-30
forum: General Help
---

### Post by spiky001 on 2011-03-30
I have A 1 user machine, User password was set when installing, can I change this password from Admin/users. Do I change the actual user password or root password? And also will this change the keyring password?

---

### Post by sisco311 on 2011-03-30
Yes, users are allowed to change their password. 

As an admin user, you can use your password for two (different) things:
[list]
[*]authenticate yourself as a normal user (log in, change your password, change your default shell...)
[*]authenticate yourself as an admin in order to run applications as another user or root (sudo, gksu)
[/list]

By default, the root account password is locked. Check out:
[uhelp]community/RootSudo[/uhelp]

You can change the keyring password with seahorse:  System -> Administration -> Passwords and Encryption Keys

---

### Post by Krytarik on 2011-03-30
> **sisco311 said:**
> 
You can change the keyring password with seahorse:  System -> Administration -> Passwords and Encryption Keys
It may also be "Applications -> Accessiores -> Passwords and Encryption Keys" instead, at least that's the case in 10.04.

Greetings.

---

### Post by sisco311 on 2011-03-30
> **Krytarik said:**
> It may also be "Applications -> Accessiores -> Passwords and Encryption Keys" instead, at least that's the case in 10.04.

Greetings.

It could be. I was too lazy to check it. :) 

Just chrooted into Natty and it's under "System ->  Preferences".

Who knows? :P

Anyway, the command to start it is:
```
seahorse
```

---


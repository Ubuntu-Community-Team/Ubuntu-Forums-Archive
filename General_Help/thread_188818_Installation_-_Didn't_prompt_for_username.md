---
title: "Installation - Didn't prompt for username"
date: 2006-06-04
forum: General Help
---

### Post by nerdymark on 2006-06-04
Good afternoon everyone,
Silly question: I just went through the install and for some reason, it either didn't ask me for a user name, or I breezed past it without noticing... What's the default user name? I set the password for it, but I don't remember seeing a username field at all... 

Help! :)

---

### Post by mlind on 2006-06-04
You need to boot on recovery mode, GRUB boot menu should contain recovery option.

After booting, you should be logged as root. Check if /etc/passwd file contain
user with user-id (UID) 1000. It's the first integer on each line.

If not, you must manually create new user and assign it to required groups
(replace username with the name you want)

```

adduser -uid 1000 *username*

```

Add new user to following groups, also to group that's same as your username
(Ubuntu default)
```

*username* adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin 

```

Using
```

adduser user group

```

---

### Post by nerdymark on 2006-06-04
Brilliant! Thank you VERY much. when viewing the passwd file, I saw a line for OEM. I guess I installed in OEM mode :)

---

### Post by mlind on 2006-06-04
[QUOTE=nerdymark]Brilliant! Thank you VERY much. when viewing the passwd file, I saw a line for OEM. I guess I installed in OEM mode :)[/QUOTE]

Looks like it yeah :mrgreen: 
you can do *deluser OEM* to get rid of it.

---


---
title: "gpg error: unsafe permissions on configuration file."
date: 2009-12-11
forum: General Help
---

### Post by themusicalduck on 2009-12-11
I'm trying to add a key with the command ```
gpg --keyserver keyserver.ubuntu.com --recv 55708F1EE06803C5

```

But I get this error - 

```
gpg: WARNING: unsafe permissions on configuration file `/home/theo/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/theo/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

The permissions on gpg.conf is Owner theo - read and write, group theo - read and write, Others - none.

There doesn't seem to be much info on this in google.. anyone have an idea how to fix it? I'm using 9.10.

---

### Post by themusicalduck on 2009-12-11
bump

edit: Nevermind, fixed it with these commands

chmod 600 ~/.gnupg/gpg.conf
chmod 700 ~/.gnupg

---


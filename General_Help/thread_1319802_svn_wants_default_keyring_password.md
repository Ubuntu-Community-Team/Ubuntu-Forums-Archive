---
title: "svn wants default keyring password"
date: 2009-11-08
forum: General Help
---

### Post by Seine on 2009-11-08
Hello

With a fresh Karmic install, svn requires password for default keyring. The SU password does not work. Blank password does not work.

```
jem@support-01:~$ svn ls svn://192.168.100.1/support/
Password for 'default' GNOME keyring: 
svn: GNOME Keyring is locked and we are non-interactive
```

This is the first time I've had a problem with svn since starting with Ubuntu Dapper Drake. What can I do here?

---

### Post by Seine on 2009-11-08
Edit ~/.subversion/config
In section [Auth] add:
```
password-stores =
```

---


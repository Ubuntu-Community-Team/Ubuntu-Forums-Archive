---
title: "Error when sharing folders"
date: 2009-08-30
forum: General Help
---

### Post by Kasam on 2009-08-30
Hi, This is the first time i`v tried Ubuntu/Linux. Being a long time Windows user i must say, Linux is not as bad as i thought it would be. But Im having problems sharing folders. I keep getting this error:


[FONT=monospace]'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


I`v already installed Samba. Anyone know how to fix this?

Thanks
[/FONT]

---

### Post by Liolikas on 2009-08-30
You have to set correct permissions in file/folder properties. In order to avoid compromised access Linux file systems have POSIX capabilities. Windows still use 50 years old magnetic tape style system without security.

---

### Post by drs305 on 2009-08-30
You can install system-config-samba which provides a graphical method of setting up samba shares:
```

sudo apt-get install system-config-samba

```
Then System > Administration > Samba

---


---
title: "use samba4 or installing an older version"
date: 2010-08-15
forum: General Help
---

### Post by ninetails on 2010-08-15
On Ubuntu 10.04 samba4 is what gets installed when trying to install samba. All instructions I've found on the net found say pretty much the same thing about how to setup samba. The problem is those instructions don't work for samba4. In samba4 the following lines are not recognized in the smb.conf file:

```
read only = no
guest ok = yes
```

From what I've read these are valid statements in older versions of samba. Not so in samba4. The smb.conf file that gets installed with samba4 is not updated. Furthermore, smbpasswd does not work and sudo /etc/init.d/samba restart does not work either, since samba is not located /etc/init.d.

How do I uninstall samba4 and install samba3?

---


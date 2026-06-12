---
title: "Help Samba Sever"
date: 2012-02-05
forum: General Help
---

### Post by cybercity@localhost on 2012-02-05
my samba service status shows

```
Global parameter guest account found in service section
```samba server is working well but i don't know why this Notice appears in my server status?


and one more thing i want to ask that my server reveals my shared directories although they are password protected but whenever any user connects to my server it asks for password on directories only.

---

### Post by luvshines on 2012-02-05
> **cybercity@localhost said:**
> my samba service status shows

```
Global parameter guest account found in service section
```samba server is working well but i don't know why this Notice appears in my server status?

Maybe your smb.conf file has 'guest account' parameter written under some share section

If you look into the man page, (G) denotes that this has to be under [global] section in your smb.conf> 
guest account (G)

---


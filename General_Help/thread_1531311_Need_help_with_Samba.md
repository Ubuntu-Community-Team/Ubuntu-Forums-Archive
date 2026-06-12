---
title: "Need help with Samba"
date: 2010-07-14
forum: General Help
---

### Post by neon401 on 2010-07-14
Hey folks,

I'm having some problems configuring Samba properly.
I will try to explain how I want it;


[LIST=1]
[*]Share [wd] with everyone, read-only for guests, writable for Windows user Oscar (I guess I have to add the Windows user to the Linux OS somehow)
[*]Share [www] only with Oscar, require username/password.
[/LIST]

This is how my smb.conf looks now. My cluelessness is probably apparent enough :p
```
[global]
workgroup = NALUM
netbios name = TRULS
server string = SAMBA server
security = share
local master = yes
os level = 35
guest account = nobody

[wd]
comment = Western Digital Essentials 1TB
path = /mnt/wd
public = yes
write list = Oscar

[www]
comment = www
path = /var/www
valid users = Oscar
writable = yes


```

Thanks a lot for any help!

---

### Post by beatdawookie on 2010-07-14
what version of windows are you using?

---

### Post by neon401 on 2010-07-14
> **beatdawookie said:**
> what version of windows are you using?
Windows 7 Ultimate x64

---

### Post by beatdawookie on 2010-07-14
See if this helps...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

or this...

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by neon401 on 2010-07-14
> **beatdawookie said:**
> See if this helps...

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

or this...

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)
I'm sorry, I still can't get it to work :/

I'm a bit of a Linux newbie, sadly.

**EDIT:** I managed to solve it!

This is how my smb.conf looks now, and it works great.

```

[global]
   workgroup = NALUM
   netbios name = truls
   security = share
   guest account = nobody

[www]
  comment = www
  path = /var/www
  browseable = yes
  valid users = Oscar
  write list = Oscar

[wd]
  comment = WD1TB
  path = /mnt/wd
  browseable = yes
  write list = Oscar
  guest ok = yes



```

---


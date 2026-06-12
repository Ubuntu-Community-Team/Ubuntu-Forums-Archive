---
title: "Samba Sharing With Unique Users Permissions"
date: 2011-08-30
forum: General Help
---

### Post by sdoolman on 2011-08-30
[B]Hello,

Say I wanted to share a folder called "share" but limit the access of any valid user. For example, user "ubuntu" would have full 'r/w' access but user "guest" would have only 'r' access. Is that possible to implement in smb.conf file?

Thanks in advance,

Sdoolman

;-)
[/B]

---

### Post by Morbius1 on 2011-08-30
I like to solve these kinds of problems in a way that doesn't require me to think too much so I would offer the following suggestion:

Create 2 shares pointing to the exact same target folder but with different share names and different access permissions. For example:

```
[share-guest]
path = path/to/folder
guest ok = yes
read only = yes

``````
[share-write]
path = path/to/folder
guest ok = no
read only = no
```Everyone will have read only access to "share-guest" but only those who have samba user names and passwords will have write access to "share-write"

You can further limit access to [shares-write] by declaring a subset of the samba users:
```
[share-write]
path = path/to/folder
guest ok = no
valid users = ubuntu
read only = no
```

---

### Post by Wayne_V on 2011-08-30
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2611888](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html#id2611888)

---

### Post by sdoolman on 2011-08-30
[B]Thanks, I'll Try!

Update: it's working, also added under [global]:
```

security = share

```

and under [share-guest]:
```

guest account = ftp
guest only = Yes

```
[/B]

---


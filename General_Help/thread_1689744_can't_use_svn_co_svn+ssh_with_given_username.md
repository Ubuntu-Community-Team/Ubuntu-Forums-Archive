---
title: "can't use svn co svn+ssh with given username"
date: 2011-02-17
forum: General Help
---

### Post by phun-ky on 2011-02-17
Basically i'm trying to do this

```
DOMAIN\other_user_name@localhost:~& svn co svn+ssh://user_name@repository_hostname/home/svn/myproject myproject --username user_name
```

But the --username is ignored and I still get prompted to enter the password for DOMAIN\other_user_name:

```
DOMAIN\other_user_name@repository_hostname's password:
```

I want this to happen:

```
user_name@repository_hostname's password:
```

Anyone got any idea on how I can get this to work?

---


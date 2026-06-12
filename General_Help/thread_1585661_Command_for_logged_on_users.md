---
title: "Command for logged on users"
date: 2010-09-30
forum: General Help
---

### Post by Jonny87 on 2010-09-30
Just wondering is there a command that would show me the details of whose currently logged on and how their logged on i.e. ssh/samba etc?

---

### Post by cj.surrusco on 2010-09-30
The 'users' command will show any users that are logged in, but I'm not sure how to find out *how* they are logged in.

---

### Post by Jonny87 on 2010-09-30
> **cj.surrusco said:**
> The 'users' command will show any users that are logged in, but I'm not sure how to find out *how* they are logged in.

Sorry should have mentioned that I was aware of that command but was looking for something that gives more details. Thanks anyway.

---

### Post by CharlesA on 2010-09-30
> **Jonny87 said:**
> Sorry should have mentioned that I was aware of that command but was looking for something that gives more details. Thanks anyway.

The "who" and "w" commands give a bit more detail, I believe.

---

### Post by Jonny87 on 2010-09-30
> **CharlesA said:**
> The "who" and "w" commands give a bit more detail, I believe.

Thanks this look just like what I'm after. I wait a few mins in-case someone knows of any other commands that are worth knowing then I'll mark it solved. Thanks for your help.

---

### Post by Herman on 2010-10-01
This will tell you how they are logged in, (ssh perhaps), including their IP addresses, and dates and times of connections and disconnects.
```
less /var/log/auth.log
```EDIT:
or maybe this one would be a little bit better, but will be specific to SSH logins only,
```
less /var/log/auth.log | grep sshd
```

---


---
title: "Mozilla Firefox: http://localhost:51302"
date: 2010-06-23
forum: General Help
---

### Post by ajack38 on 2010-06-23
Hi, I recently installed ubuntu 10.04 and every time I open Firefox it comes up with: A username and password are being requested by [http://localhost:51302](http://localhost:51302). The site says: "administrator"

I tried my login password and my ubuntu-one password and they didn't work. If anyone might know what the password could be then can you please reply.

Thanks.

---

### Post by CharlesA on 2010-06-23
You can check to see what's running by running this in a terminal:

```
netstat -l
```

---

### Post by lovinglinux on 2010-06-23
> **ajack38 said:**
> Hi, I recently installed ubuntu 10.04 and every time I open Firefox it comes up with: A username and password are being requested by [http://localhost:51302](http://localhost:51302). The site says: "administrator"

I tried my login password and my ubuntu-one password and they didn't work. If anyone might know what the password could be then can you please reply.

Thanks.

[http://localhost](http://localhost) means you are trying to access a local server. What server do you have installed?

You can change the initial page in Firefox preferences.

---

### Post by ajack38 on 2010-06-25
Don't worry about this, i just decided to reinstall ubuntu 10.04 and it didn't come up again.

---


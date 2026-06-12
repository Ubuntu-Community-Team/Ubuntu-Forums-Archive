---
title: "flumotion username / password any one figured it our ?"
date: 2006-06-05
forum: General Help
---

### Post by oly on 2006-06-05
wanted to have a play with this software but on both breezy and dapper it asks for a username and password, any one figured out what it is ??

or no where to reset it ??

---

### Post by gonçalo on 2006-07-14
me too!

tried my own and the "user" "test" they mention in the flumotion web page. still nothing...

---

### Post by LKRaider on 2006-09-11
Be sure you started the flumotion service first:
```
sudo invoke-rc.d flumotion start
```

Then try to login with username: user password: test



You can also change the default username and password by editing the worker file:
```
gksudo gedit /etc/flumotion/workers/default.xml
```

---


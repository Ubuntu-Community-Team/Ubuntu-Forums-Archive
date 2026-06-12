---
title: "MySQL &amp; PHP - Access denied ( even root account doesn't work )!"
date: 2009-09-02
forum: General Help
---

### Post by credobyte on 2009-09-02
A fresh install of Ubuntu 9.04 ( Jaunty ).

```
[COLOR=Red][MySQL] Access denied for user 'root'@'localhost' (using password: YES)[/COLOR]
```

The problem is that, no matter what I do, I can't access MySQL from PHP. Even root account fails to connect .. 
What could be the problem ? The weirdest thing is that .. phpMyAdmin is still up and running ( I even tried to add a few demo users with/without passwords ).

MySQL:
```
mysql  Ver 14.12 Distrib 5.0.75, for debian-linux-gnu (i486) using readline 5.2
```

Apache:
```
Server version: Apache/2.2.11 (Ubuntu)
Server built:   Aug 18 2009 14:26:31
```

---

### Post by cranecreek on 2009-09-02
A little more info might help

[COLOR=Red](using password: YES)[/COLOR]
Did you give php a root pw? Are you using the server version of Ubuntu? Did you use apt-get to install or from the the php site. Try logining in with no pw, If that doesn't work post back

If your planning on hosting more than one site take a look at [this]("http://howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3")

---

### Post by brian3 on 2009-09-03
i had this problem once, the best bet is to delete and start again

---

### Post by wojox on 2009-09-03
What happens if you shutdown phpmyadmin and login from the terminal?

---

### Post by credobyte on 2009-09-03
Problem solved by reinstalling the whole LAMP stack. I was able to login into MySQL administrator, I was able to use phpMyAdmin .. I wasn't able to use it anywhere else.

---


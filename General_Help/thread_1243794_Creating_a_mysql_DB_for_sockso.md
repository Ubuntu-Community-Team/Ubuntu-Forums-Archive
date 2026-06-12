---
title: "Creating a mysql DB for sockso"
date: 2009-08-18
forum: General Help
---

### Post by terry f on 2009-08-18
Im trying to get sockso to use mysql for its DB backend.  I found a guid for installing mysql, I skiped step two because Im not using PHP.  But when I went to creat a DB in step three I got an error.  Can someone tell me what I doing wrong.

Guild Im using link: [http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/")

Error Im getting:
```
terry@terry-ubuntu-desktop:~$ mysqladmin create musicDB
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'terry'@'localhost' (using password: NO)'

```

---

### Post by terry f on 2009-08-19
any one?

---

### Post by DaithiF on 2009-08-19
Hi,
did you specify a root password for mysql when you installed it?
if so
```
mysqladmin -h localhost -u root -ppassword create musicDB

```

---


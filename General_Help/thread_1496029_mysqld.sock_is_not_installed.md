---
title: "mysqld.sock is not installed"
date: 2010-05-28
forum: General Help
---

### Post by Bietje on 2010-05-28
Why mysqld.sock not installed when i compile mysql from sources? Actualy the entire var directory is missing.

I tried the following configures:

```
./configure --prefix=/opt/server/mysql --with-mysqld-user=mysql

./configure --prefix=/opt/server/mysql --localstatedir=/opt/server/mysql/var --with-unix-socket-path=/opt/server/mysql/var/mysql.sock --with-mysqld-user=mysql
```Where does it go wrong? Im trying to compile mysql version 5.1.47

Thanks

---


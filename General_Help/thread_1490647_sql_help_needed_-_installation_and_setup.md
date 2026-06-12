---
title: "sql help needed - installation and setup"
date: 2010-05-22
forum: General Help
---

### Post by tckotb on 2010-05-22
I installed mysql-client, server, and common, and php5-mysql. When i use the command: 

> "mysqladmin -u root password 'password'"

to setup my account i get this:

> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by wojox on 2010-05-22
Try this:

```
mysql -u root -p
```

Then it will prompt you for your password.

---

### Post by tckotb on 2010-05-28
i get the same error, it's says root@localhost does not have access

---


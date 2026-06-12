---
title: "mysql client &amp; server"
date: 2010-11-12
forum: General Help
---

### Post by oren tal on 2010-11-12
I have installed mysql client and server on my ubuntu.
However they are not in the application menu.

How do I start them and access to them?
Right now I can not use them.

---

### Post by carl.davis on 2010-11-12
Hello,

MySQL server usually starts after installation. You can access it via opening gnome-terminal and then typing 

```
mysql -u root -p
```

You will then be asked for the password you created during MySQL's installation.

You could also install phpmyadmin. After that is installed you can use Firefox and browse to "http://127.0.0.1/phpmyadmin" to get a more graphical view of the database server, databases and tables.

---

### Post by oren tal on 2010-11-12
> **carl.davis said:**
> Hello,

MySQL server usually starts after installation. You can access it via opening gnome-terminal and then typing 

```
mysql -u root -p
```

You will then be asked for the password you created during MySQL's installation.

You could also install phpmyadmin. After that is installed you can use Firefox and browse to "http://127.0.0.1/phpmyadmin" to get a more graphical view of the database server, databases and tables.

Thanks.

---


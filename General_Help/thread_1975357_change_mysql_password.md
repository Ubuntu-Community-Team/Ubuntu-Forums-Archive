---
title: "change mysql password"
date: 2012-05-07
forum: General Help
---

### Post by dpuk44 on 2012-05-07
when i installed apache, mysql and phpmyadmin i set the mysql password to 'test' (doh!)

how can i change this to '' (nothing)

thanks

---

### Post by Cheesemill on 2012-05-07
To change the MySQL root password do:
```
mysqladmin -u root -p'oldpass' password 'newpass'
```Why do you want a blank password? That is a very bad idea.

---

### Post by dpuk44 on 2012-05-07
because all the mysql, php tutorials use a blank password for example there connection strings seem to be $con = mysql_connect

("localhost","root","");

?

---

### Post by codemaniac on 2012-05-07
> **dpuk44 said:**
> because all the mysql, php tutorials use a blank password for example there connection strings seem to be $con = mysql_connect

("localhost","root","");

?

However it is not a good idea to keep root Mysql password blank .You always have the option to pass user and password while connecting to mysql from your script .

---


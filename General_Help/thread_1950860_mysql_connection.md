---
title: "mysql connection"
date: 2012-04-01
forum: General Help
---

### Post by kswix on 2012-04-01
Hi all!

I use a mysql. It worked for me for half-year, but today...

I didn't change anything (or I don't remember, because of I used mysql many times ago)

When I run emma from abr user (I used it before), I get Access denied for root@localhost (USING PASSWORD: NO) (it successfully connected before). 

After googling, I find command:
> abr@misha:~/projects/2012/personlab$ sudo mysqladmin -u root password ''
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
but it don't work too!

What going wrong? Please help, I work on contract, which require mysql.

UPD: Upgrading of mysql-client, mysql-server don't help me.

Is there way to remove the db and create again?

Regards,
Alex

---

### Post by kswix on 2012-04-01
SOLVED: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---


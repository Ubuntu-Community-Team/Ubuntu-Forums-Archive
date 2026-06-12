---
title: "phpmyadmin wont login"
date: 2012-08-01
forum: General Help
---

### Post by amabam on 2012-08-01
Hi, I am having a terrible time getting phpmyadmin working. I have had it working for the past year and a half and have not accessed it in a good few months. But now when I go to mysite/phpmyadmin i get a login box and enter my details and it wont accept them.

I have tried changing my root mysql password with no success in loggin in to phpmyadmin. Mysql command logs in from the console and my website successfully connects to the mysql server.

I have checked the apache2 error log and have found this line:

[Wed Aug 01 12:00:30 2012] [error] [client 127.0.0.1] user root not found: /phpmyadmin

I have checked in my webmin admin panel that the root user is there in the mysql module.

What else can I check to debug the problem? I have tried removing phpmyadmin, mysql-server and all dependencies and purging the config files and then reinstalling with the same problems.

I hope someone can help as all the other forum posts I have googled have not came up with any solutions that work for me.

Thanks in advance

EDIT: I am running Ubuntu Server 10.04 on my VPS

---

### Post by amabam on 2012-08-02
Can nobody help me?

---

### Post by ijumpship on 2012-08-03
phpMyAdmin is just a front end to mysql.most time this occur you have chosen a blank password  for the mysql root and phpmyadmin does not allow blank password.
therefore try setting a password for your mysql by doing this

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

---

### Post by amabam on 2012-08-04
> **amabam said:**
> I have tried changing my root mysql password with no success in loggin in to phpmyadmin. Mysql command logs in from the console and my website successfully connects to the mysql server.

In my original post you can see if you read it that I have tried changing my password. The problem is with phpmyadmin, not mysql as I can login with my website using the correct password and using the mysql console. Phpmyadmin will not login using any password.

---

### Post by Amigo Chan on 2012-08-13
Try to reconfigure phpmyadmin, and reset MySQL password.

1. Ctrl + Alt + T to launch terminal
2. sudo dpkg-reconfigure phpmyadmin
3. Connection method for MySQL database for phpmyadmin: unix socket
4. Name of the database's administrative user: root
5. Password of the database's administrative user: mysqlsamplepassword
6. MySQL username for phpmyadmin: root
7. MySQL database name for phpmyadmin: phpmyadmin
8. Web server to reconfigure automatically: apache2
9. ERROR 1045
10. ignore
11. sudo dpkg-reconfigure mysql-server-5.5
12. New password for the MySQL "root" user: mysqlsamplepassword
13. Repeat password for the MySQL "root" user: mysqlsamplepassword

Wish it helps!

Have a nice day!

---


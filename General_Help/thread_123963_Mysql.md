---
title: "Mysql"
date: 2006-01-31
forum: General Help
---

### Post by seekyrr on 2006-01-31
Looking for a command/method to reset mysql root password.

I type mysql -u root -p and type my password.

Error 1045 Access denied for user : 'root@localhost' (Useing password: YES)

Thanks

Seek

---

### Post by seekyrr on 2006-01-31
Opps ..I figured this one out..Thanks

Seek

---

### Post by yanik on 2006-01-31
Could you share your solution with us?

---

### Post by seekyrr on 2006-01-31
Silly me had root with no password for mysql

Just loged in without the -p and it went great.

The problem now seems to be access rights to the database.  I have gone into webmin for SQL, verified the user permisions and database rights for the user...but I keep getting denied access.

I nuked the database, redid everything and same error.  Not sure where else it could possibly be lookin for a password.

Actual error is:[B]Warning :mysql_pconnect() Access denied for user 'snort@localhost" in /usr/share/adodb/drivers/adodb-mysql.inc.php

Error (p) connecting to DB : snort@localhost

Database Error:Access denied for user snort@localhost[/B]


Seek

---

### Post by ZylGadis on 2006-01-31
You should take a look at the mysql database (login as root of course) - this is where mysql keeps its permissions. I guess you would be particularly interested in mysql.user and mysql.db. Note: '%' in mysql terms means "any host."
Also, you can safely browse it, but don't modify anything there directly if you don't know what you are doing - passwords are hashed, and you need to remember to flush privileges. Use the GRANT and REVOKE sql syntax to change anything.
Hope that helps.

---

### Post by seekyrr on 2006-01-31
Thanks for the info.  On a hunch I made a new user and left the password blank.

It worked.

So I went and removed the password from my trouble account.  It worked too.

It seems not to be able to read the encrypted password file?

Seek

---

### Post by Nibuzer on 2006-02-10
Hi everybody,

I dont know if I can post here...

well, I am looking for the right version of mysql for my ubuntu 5.10

Could you help me?

thanks a lot

bye

---


---
title: "mysql error 1045... i have tried all"
date: 2009-07-05
forum: General Help
---

### Post by babbar.ankit on 2009-07-05
I have googled everthing tried to give every command but the reply is same:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
 I have tried all those try to change password or ny hel advice on d forumz..
It has beeen mor dn 24 hrs of struggling but mysql don't work 
Plz help asap...

---

### Post by yogeshg1987 on 2009-08-03
I had the same problem, It could be a problem with permissions. There are two ways, either you have to reset the password for mysql.

```
:~$ mysql -u root -p

``` then give the password if it asks.

Then 

```
mysql> SET PASSWORD FOR yourusername@yourhost_usually_localhost = PASSWORD('YOURPWD');
```

If it doesn't work out, you might have to set permissions to the mysql directory. Set 711 or 751 to mysql directory at "/var/lib/mysql/mysql".

Here's how:

```
 $ sudo chmod 711 /var/lib/mysql/mysql 
```

Hope this helps,
Yogesh.

---


---
title: "Cannot access mysql as new user"
date: 2009-08-14
forum: General Help
---

### Post by CarltonF on 2009-08-14
I installed Intrepid server on my web server and I have this issue. The default user is named root. I wanted to make a new user with my own name, since that it what I used on my old server, plus I don't want to be using the root account in my web pages. I looked in the user table in the mysql database and saw 3 entries for root, all with the same data except for the host names.

I added a new user which was just a clone of this, with the host as localhost and the username changed for mine, so it looks like so:

```
+-----------+--------+-------------------------------------------
| Host      | User   | Password 
+-----------+--------+-------------------------------------------
| localhost | root   | *6E7C17B56F9A7SB26256347647268793AA9E5C2B 
| ctnserv   | root   | *6E7C17B56F9A7AB26256347647268793AA9E5C2B 
| 127.0.0.1 | root   | *6E7C17B56F9A7AB26256347647268793AA9E5C2B 
| localhsot | Carl   | *6E7C17B56F9A7AB26256347647268793AA9E5C2B

```
When I try to access mysql I get the following error:
> carlton@ctnserv:~$ mysql -uCarl -p[mypass] -hlocalhost mysql
ERROR 1045 (28000): Access denied for user 'Carl'@'localhost' (using password: YES)

Now I know the password is correct because I can log in fine on the root account with it. I tried each of the three different host names with the Carl account but I get the same error every single time.

Can anyone help me out with this?

---

### Post by soapBAR2 on 2009-08-14
Are you part of the mysql group?

```
sudo useradd -G mysql Carl
```

I believe that by default, this is all you need for mysql.

---

### Post by techstop on 2009-08-14
Why are you editing the tables directly to add a new user (instead of issuing the 'CREATE USER' command)?

You have also misspelled 'localhost' in this line;
```

localhsot | Carl   | *6E7C17B56F9A7AB26256347647268793AA9E5C2B
```

Once you have a user correctly added, you need to 'GRANT' privileges.

You might need to 'FLUSH PRIVILEGES' as well.

[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

---

### Post by CarltonF on 2009-08-15
Thanks for the help, I will try those suggestions.

I was adding a user directly because I followed the instructions at [http://www.php-mysql-tutorial.com/wikis/mysql-tutorials/add-new-mysql-user.aspx](http://www.php-mysql-tutorial.com/wikis/mysql-tutorials/add-new-mysql-user.aspx)

---


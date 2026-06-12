---
title: "mysql.user has many user"
date: 2010-08-19
forum: General Help
---

### Post by jaya28inside on 2010-08-19
greetings everyone,

since I can not post to Ubuntu Server section,
I choose this section to post about this mysql general problem.

I just checking mysql and trying to execute

```

mysql> select user from mysql.user;

```

you know what's the general or the common output?
I've not found it yet through google until now.

This is my result;

> 
+------------------+
| user             |
+------------------+
| root             |
| debian-sys-maint |
| root             |
| root             |
+------------------+
4 rows in set (0.00 sec)


but i realize, i never create debian-sys-maint
and again, i never create root user until 3 times.

Is this some error or missconcept or what?
Then if we do removing those users, 
and create 1 user (example: root)
is it safe?

If anyone could share with me about this ...

:D

---

### Post by DaithiF on 2010-08-20
Hi,
try:
select User, Host from mysql.user;

you will see that the 3 root users are not duplicates, but that each is related to a particular host, usually %, 127.0.0.1 and <yourhostname>.  Mysql doesn't just have usernames, it cares also about the machine that a user connects from.  

the debian-sys-maint user is created by debian-based distros (including ubuntu) and is used for starting/stopping the server, rotating table-based server logs.

in short nothing to worry about, you can leave them as-is.

---

### Post by jaya28inside on 2010-08-22
oh yes, u r right, DaithiF.

Now I could see it clearly, that these root account data
is not duplicated.

> 
mysql> select user,host from mysql.user;
+------------------+--------------+
| user             | host         |
+------------------+--------------+
| root             | 127.0.0.1    |
| debian-sys-maint | localhost    |
| root             | localhost    |
| root             | omega        |
+------------------+--------------+
6 rows in set (0.00 sec)


is it means everytime we do executing of 
```
GRANT USER ... bla bla bla
```

the data would be added here, right?
Hmm... would it be safe if we remove some specific user account data 
over this dB? I mean, is it safe if  
we do removing it via

```
DELETE * FROM mysql.user WHERE user = 'something' AND host = 'something'
```

command anyway?

---

### Post by DaithiF on 2010-08-23
> **jaya28inside said:**
> would it be safe if we remove some specific user account data 
over this dB? I mean, is it safe if  
we do removing it via

```
DELETE * FROM mysql.user WHERE user = 'something' AND host = 'something'
```command anyway?

its better to use the drop user statement
[http://dev.mysql.com/doc/refman/5.1/en/drop-user.html](http://dev.mysql.com/doc/refman/5.1/en/drop-user.html)

---

### Post by jaya28inside on 2010-08-23
or8,,, now it's all clear.

---


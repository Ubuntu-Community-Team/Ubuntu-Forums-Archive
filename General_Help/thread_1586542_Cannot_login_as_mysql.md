---
title: "Cannot login as mysql"
date: 2010-10-02
forum: General Help
---

### Post by Dooley on 2010-10-02
Apologies it should by **cannot login to mysql**, but I cannot rename the thread.

Hey there,

I'm having problems with a mysql install on a ubuntu server edition.

I forgot the mysql root password(or maybe it's always been screwy), so I attempted to reset the root password using this: 

```
sudo dpkg-reconfigure mysql-server-5.0
```

However this did not work.

So I decided to run

```
sudo apt-get purge mysql-server-5.0 && sudo apt-get install mysql-server-5.0
```

And re-entered the root password and again I still can't login!

This is the error I keep getting.
```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

Is there any further steps I can do to wipe this crappy mysql install?

Thanks

---

### Post by sinamorawej on 2010-10-02
Hi

This might help:
[http://www.ge.ubuntuforums.org/showthread.php?p=9846128](http://www.ge.ubuntuforums.org/showthread.php?p=9846128)

---

### Post by envygeeks on 2010-10-02
Kill MySQL off:

```

sudo pkill -f "mysql"

```

Create the file /home/username/mysql_reset_password with the contents:

```

UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;

```

Then start mysql using the following command:

```

sudo mysqld_safe --init-file=/home/username/mysql_reset_password &

```

Open a new tab then attempt to login to MySQL.
If that fails, then you can purge mysql completely doing the following:

```

sudo apt-get autoremove --purge mysql*

```

```

sudo rm -rf /var/lib/mysql

```

---

### Post by Dooley on 2010-10-02
Cheers folks!

Unfortunately I was getting nowhere with skip-grant.

I also tried your steps envy geeks  but it took a full purge and deleting the entire folder to get this install back on it's feet! Many thanks!

---


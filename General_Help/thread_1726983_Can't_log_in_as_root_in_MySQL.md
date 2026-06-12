---
title: "Can't log in as root in MySQL"
date: 2011-04-11
forum: General Help
---

### Post by sombrancelha on 2011-04-11
Hello,

I installed MySQL and I started playing around (first time using a database). I eventually ended up deleting the root user. And now I can't log back in.

I tried

```

~# apt-get remove --purge mysql-server-5.1
~# sudo apt-get install --reinstal mysql-server-5.1

```

and I was prompted to set a new root password, which I did. However...

```

~$ mysql -u root -p
Enter passsword:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

I want to do a fresh install of MySQL.

Thanks

---

### Post by bance on 2011-04-12
Try this [_[COLOR=Red]link[/COLOR]_]("https://help.ubuntu.com/community/MysqlPasswordReset").

---

### Post by sombrancelha on 2011-04-13
> **geirha said:**
> Removing and even purging mysql-server, will not remove the databases. I'm not sure if these symptoms were due to corrupt databases or otherwise, but for a really clean reinstall of mysql-server, one should also remove /var/lib/mysql/ where the database-files are stored. 

This will remove configuration files and databases, so don't use it if you don't mean it:
```

sudo aptitude purge mysql-server
sudo mv /var/lib/mysql /var/lib/mysql.backup
sudo aptitude install mysql-server
# If you are confident that you don't need the old databases around:
# rm -rf /var/lib/mysql.backup/

```

That made the trick.

---


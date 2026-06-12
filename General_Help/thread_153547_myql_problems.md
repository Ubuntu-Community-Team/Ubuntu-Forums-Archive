---
title: "myql problems"
date: 2006-04-01
forum: General Help
---

### Post by urbansurfer on 2006-04-01
All posts seem to point to mysql living here:

 /usr/local/mysql

On my in stall it does't live here.

I install mysql 4.0.64 using the synaptic package manager

Also I now cant login 

Anyone know why?

root@turtle:/usr/bin# mysql -u -p
ERROR 1045: Access denied for user: '-p@localhost' (Using password: NO)
root@turtle:/usr/bin# mysql -u mysql
ERROR 1045: Access denied for user: 'mysql@localhost' (Using password: NO)
root@turtle:/usr/bin# mysql -u mysql -p mysql
Enter password:
ERROR 1045: Access denied for user: 'mysql@localhost' (Using password: YES)
root@turtle:/usr/bin# mysql -u mysql -p mysql
Enter password:
ERROR 1045: Access denied for user: 'mysql@localhost' (Using password: YES)
root@turtle:/usr/bin# mysql -u mysql -p mysql
Enter password:
ERROR 1045: Access denied for user: 'mysql@localhost' (Using password: YES)
root@turtle:/usr/bin# mysql -u root -p
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)


Thanks

---

### Post by Akli on 2006-04-01
just type this:

sudo mysql

---

### Post by urbansurfer on 2006-04-01
I get this....

steve@turtle:/usr/bin$ sudo mysql
Password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

---

### Post by Akli on 2006-04-01
This is what I have installed:

[[IMG]http://img236.imageshack.us/img236/7327/screenshot2rd.png[/IMG]](http://imageshack.us)

Try to get the same thing, and then sudo mysql (anywhere, you don't need to to browse to usr/bin)

---

### Post by Akli on 2006-04-01
and just for fun, install apache2 and restart it, 

sudo apt-get install apache2

sudo /etc/init.d/apache2 restart

---

### Post by urbansurfer on 2006-04-01
I have the same install and get this. 

Somehow the default password is not working, shall I try re-installing it?

steve@turtle:/etc/init.d$ cd /home/steve
steve@turtle:~$ sudo mysql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

---

### Post by Akli on 2006-04-01
did you install apache2?

---

### Post by Akli on 2006-04-01
If it does not work for, try to install everything again, (php just for fun)

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
sudo /etc/init.d/apache2 restart

and then try sudo mysql

---

### Post by urbansurfer on 2006-04-01
yes 

I tried this:
 mysql -u root mysql -p myrootpassword


and got this:

mysql  Ver 12.22 Distrib 4.0.24, for pc-linux-gnu (i486)
Copyright (C) 2002 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field

etc.

Doe sthat mean I have installed it ok and just need to use the computer's root password?

---

### Post by Akli on 2006-04-01
I think there is a misunderstandi, use the password of your ubuntu session!

either that of steve or turtle.

---

### Post by Akli on 2006-04-01
Nothing

---

### Post by DoktorSeven on 2006-04-01
To set your MySQL root password if there's not one set:
```

sudo mysqladmin password desiredpassword

```

of course replacing "desiredpassword" with the one you want.

To log in as root:
```

mysql -u root -p

```
(no need for sudo)

It will then ask for the password you set above.

Resetting an unknown MySQL root password is trickier:

```

$ sudo /etc/init.d/mysql stop
$ sudo mysqld --skip-grant-tables &
$ mysql -u root
> update mysql.user set password=PASSWORD('desiredpassword') WHERE user='root';
> quit
$ sudo killall mysqld
$ sudo /etc/init.d/mysql start

```

---

### Post by urbansurfer on 2006-04-02
Thanks for your help Akli 

[http://ubuntuforums.org/showthread.php?t=135096&highlight=mysql+password+problems](http://ubuntuforums.org/showthread.php?t=135096&highlight=mysql+password+problems)

This sorted it for me. Seems lots of people are having this problem

---


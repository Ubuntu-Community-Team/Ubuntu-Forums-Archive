---
title: "Lampp mysql won't start"
date: 2010-08-04
forum: General Help
---

### Post by iShurtugal on 2010-08-04
I had xampp going, but it got messed up and mysql wouldn't start. I thought reinstalling wou;d fix it, but it didn't.


when i do:
```
sudo /opt/lampp/lampp start
```

i get:
```
Starting XAMPP for Linux 1.7.3a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
```

and my mysql error log says:

```
   	 	 	 	 	 	  100804 19:13:25 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql 
 100804 19:13:25 [Note] Plugin 'FEDERATED' is disabled. 
 #/opt/lampp/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13) 
 100804 19:13:25 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it. 
 100804 19:13:25  InnoDB: Operating system error number 13 in a file operation. 
 InnoDB: The error means mysqld does not have the access rights to 
 InnoDB: the directory. 
 InnoDB: File name /opt/lampp/var/mysql/ibdata1 
 InnoDB: File operation call: 'create'. 
 InnoDB: Cannot continue operation. 
 100804 19:13:25 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/myname-desktop.pid ended 
 100804 19:15:50 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql 
 100804 19:15:50 [Note] Plugin 'FEDERATED' is disabled. 
 #/opt/lampp/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13) 
 100804 19:15:50 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it. 
 100804 19:15:50  InnoDB: Operating system error number 13 in a file operation. 
 InnoDB: The error means mysqld does not have the access rights to 
 InnoDB: the directory. 
 InnoDB: File name /opt/lampp/var/mysql/ibdata1 
 InnoDB: File operation call: 'create'. 
 InnoDB: Cannot continue operation. 
 100804 19:15:50 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/myname-desktop.pid ended 
 100804 19:20:08 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql 
 100804 19:20:08 [Note] Plugin 'FEDERATED' is disabled. 
 #/opt/lampp/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13) 
 100804 19:20:08 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it. 
 100804 19:20:08  InnoDB: Operating system error number 13 in a file operation. 
 InnoDB: The error means mysqld does not have the access rights to 
 InnoDB: the directory. 
 InnoDB: File name /opt/lampp/var/mysql/ibdata1 
 InnoDB: File operation call: 'create'. 
 InnoDB: Cannot continue operation. 
 100804 19:20:08 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/myname-desktop.pid ended
 
```

Any and all help is appreciated!

---

### Post by WorMzy on 2010-08-04
I'm afraid that I have no experience regarding XAMPP; but have you considered installing LAMP through tasksel instead?

Simply open a terminal and run
```
sudo tasksel install lamp-server
```

and voila! You have a working native LAMP installation that can have it's various elements activated like any other daemon on Ubuntu, with a simple
```
sudo service <SERVICE NAME> start
```

e.g.

```
sudo service apache start
```

You can install additional features, such as perl, python, and ruby support by installing the related modules through apt-get or synaptic, e.g.
```
sudo apt-get install apache2-mod-perl2 apache2-mod-python apache2-mod-ruby
```

I believe that you'll need to have the various related programming languages install too.

---

### Post by Ocxic on 2010-08-04
100804 19:20:08 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it. 

I suggest you run "mysql_upgrade"

---

### Post by iShurtugal on 2010-08-07
nvm, I installed apache, mysql, and php5 from synaptic and now they're working fine!  tanks for the help!

---


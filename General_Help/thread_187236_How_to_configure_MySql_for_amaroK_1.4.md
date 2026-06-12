---
title: "How to configure MySql for amaroK 1.4?"
date: 2006-06-02
forum: General Help
---

### Post by Marcos.Rufino on 2006-06-02
Does anyone know what I should do? I have mysql 4.1 installed already.

Thanks

---

### Post by linuchsan on 2006-06-02
There is a nice howto @ [http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

---

### Post by Skye on 2006-06-02
I've always wondered what the advantages were to using Mysql on amarok as opposed to Postrege (sp?) or whatever else amarok uses- could someone explain it to me?  Thanks.

---

### Post by eqisow on 2006-06-02
MySQL is faster, but this really only matetrs for huge music collections.

---

### Post by Skye on 2006-06-02
Makes sense.  Thanks, eqisow.

---

### Post by adamkane on 2006-06-07
Mysql 4.1 isn't well supported on ubuntu. Consider using mysql 4.0 or mysql 5.0:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

Create a new database called amarok. Add a new user for the database. Enter the info in amarok, and rescan collection.

---

### Post by raydekok on 2006-06-25
> Create a new database called amarok. Add a new user for the database. Enter the info in amarok, and rescan collection.

how do i do that.

mysql is running. i installed it with xampp and it works i think.

---

### Post by raydekok on 2006-06-25
o and i use kubuntu but that's isn't a problem i think

---

### Post by dorcssa on 2007-01-21
So, I installed mysql and followed the instructions..but I got confused...I think I made some mistake, I don't know what. After that, mysql only say an error ```
me@desktop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: N O)
me@desktop:~$ mysql ERROR 1045 (28000): Access denied for user 'me'@'localhost' (using password: NO) 
``` Khmm, now what? I uninstalled it many times trough synaptic with full remove, but it doesn't help. What should I remove? I don't want to screw up my system(again, I had to reinstall it once) I can live without mysql, but it would nice to use it for amarok, I have a collection about 17 gigs, not so much but no so tiny too I think.

---

### Post by Ramses de Norre on 2007-01-21
If you've already set a root password for mysql you'll need to do **mysql -p -u root** and enter the password.

---

### Post by dorcssa on 2007-01-21
Yes, I think so, but I mixed it up I think, and don't know the password now. So I want to start over. How can I remove the whole configuration setup, so next install I can setup a new password?

---


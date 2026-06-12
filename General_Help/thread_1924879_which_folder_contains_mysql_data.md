---
title: "which folder contains mysql data?"
date: 2012-02-13
forum: General Help
---

### Post by qwertyjjj on 2012-02-13
I have to restore data from a tarred backup.
Some of the data is included in /var/www, which should be easy enough.
However, I have some mysql data on there, how can I restore that - what folders do I need?

---

### Post by Khayyam on 2012-02-13
qwertyjjj ...

They are stored in a database file under /var/lib/mysql, but if you need to backup you should use mysqldump .. see [Backing up and restoring your MySQL Database](http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/) on the MySQL website.

HTH ...

---

### Post by qwertyjjj on 2012-02-13
> **Khayyam said:**
> qwertyjjj ...

They are stored in a database file under /var/lib/mysql, but if you need to backup you should use mysqldump .. see [Backing up and restoring your MySQL Database](http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/) on the MySQL website.

HTH ...

Thanks, I will do that in future but for the moment it is store din a tarball.
So, can I just copy the whole /var/lib/mysql folder from the tarball to the hard drive? Will that work, what about password settings and that kind of thing?

---

### Post by Khayyam on 2012-02-13
> **qwertyjjj said:**
> So, can I just copy the whole /var/lib/mysql folder from the tarball to the hard drive? Will that work, what about password settings and that kind of thing?

Remember mysql is live so copying the data files is not a good idea. You could shutdown mysql then make a copy but then all services that rely on mysql will go bumpity. it's best to use mysqldump ... its a diddle.

Here is the script I'd written to do this .. run as 'root'

```
#!/bin/bash

echo ""
echo " Dumping MySQL data"

if [[ ! -d /root/SQL_backups ]]; then
    mkdir /root/SQL_backups
fi

mysqldump \
  --password='your_mysql_pass' \
  -hlocalhost \
  --all-databases \
  --opt \
  --allow-keywords \
  --flush-logs \
  --hex-blob \
  --master-data \
  --max_allowed_packet=16M \
  --quote-names \
  --result-file=/root/SQL_backups/backup-$(date +%F).sql
```

HTH ...

Ab scriptum: ment to mention, this creates a dated backup file, so you can run every day.

---

### Post by qwertyjjj on 2012-02-13
> **Khayyam said:**
> Remember mysql is live so copying the data files is not a good idea. You could shutdown mysql then make a copy but then all services that rely on mysql will go bumpity. it's best to use mysqldump ... its a diddle.

Here is the script I'd written to do this .. run as 'root'

```
#!/bin/bash

echo ""
echo " Dumping MySQL data"

if [[ ! -d /root/SQL_backups ]]; then
    mkdir /root/SQL_backups
fi

mysqldump \
  --password='your_mysql_pass' \
  -hlocalhost \
  --all-databases \
  --opt \
  --allow-keywords \
  --flush-logs \
  --hex-blob \
  --master-data \
  --max_allowed_packet=16M \
  --quote-names \
  --result-file=/root/SQL_backups/backup-$(date +%F).sql
```HTH ...

But I can't use mysqldump because all the data is stored in the tarball on an external USB drive?
The current mysql server on the hard drive is empty.

---

### Post by SeijiSensei on 2012-02-13
You can restore /var/lib/mysql from backup, and it should work fine.  You will need to shutdown the server while you do so however.

```
sudo service mysql stop
sudo mv /var/lib/mysql /var/lib/mysql.bad
sudo rsync -av /path/to/backup/var/lib/mysql /var/lib
sudo service mysql start

```

You'll lose any data entered since the backup was made, of course, including any new users or databases created since then.

I posted a script to back up MySQL with mysqldump [here](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3).  You can add the array of command-line switches that Khayyam posted if you like, though I've not had problems with backups made with the defaults.  You might look into rsync as a method for storing remote copies of the data after backup as well.

---

### Post by Khayyam on 2012-02-13
> **qwertyjjj said:**
> But I can't use mysqldump because all the data is stored in the tarball on an external USB drive? The current mysql server on the hard drive is empty.

OK, so your best bet is to restore the databases from the files in the tarball. Simply shutdown mysql move (or remove) /var/lib/mysql, replace with the data files from the backup. Make sure its still owned by mysql, if not correct it. I assume Ubuntu uses mysql:mysql but you may want to check (chown -R mysql:mysql /var/lib/mysql). Restart mysql.

Note that doing this will change the password for the mysql root user to those of the previous mysql incarnation. So, be sure you have that password before doing this.

Had you a dump you could have restored from the *.sql file without any worries.

HTH ...

ps. no need to quote the whole message, just the section your replying to if need be.

---

### Post by qwertyjjj on 2012-02-14
There also seems to be a folder under /home/.mysql
Is that important?

---

### Post by Khayyam on 2012-02-14
> **qwertyjjj said:**
> There also seems to be a folder under /home/.mysql. Is that important?

No, mysql annoyingly stores its 'history' there, including passphrases. I generally remove it after a session.

```
mysql -u user -p && rm ~/.mysql
```

By the way, you did mean $HOME/.mysql and not /home right? No one should be writing dotfiles to /home/

HTH ...

---

### Post by qwertyjjj on 2012-02-14
> **SeijiSensei said:**
> You can restore /var/lib/mysql from backup, and it should work fine.  You will need to shutdown the server while you do so however.

```
sudo service mysql stop
sudo mv /var/lib/mysql /var/lib/mysql.bad
sudo rsync -av /path/to/backup/var/lib/mysql /var/lib
sudo service mysql start

```

You'll lose any data entered since the backup was made, of course, including any new users or databases created since then.

I posted a script to back up MySQL with mysqldump [here](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3).  You can add the array of command-line switches that Khayyam posted if you like, though I've not had problems with backups made with the defaults.  You might look into rsync as a method for storing remote copies of the data after backup as well.

Why this bit:
sudo rsync -av /path/to/backup/var/lib/mysql /var/lib

---

### Post by SeijiSensei on 2012-02-14
> **qwertyjjj said:**
> Why this bit:
sudo rsync -av /path/to/backup/var/lib/mysql /var/lib

I use rsync for most bulk copying tasks.  That command should copy the entire mysql directory from backup into /var/lib.  You can use "cp -a" if you prefer.

---

### Post by Khayyam on 2012-02-14
> **qwertyjjj said:**
> [QUOTE=SeijiSensei;11686330]```
sudo rsync -av /path/to/backup/var/lib/mysql /var/lib
```
Why this bit?[/QUOTE]

Why quote the whole message (when your only reponding to one section of it), and then re-quote that section? Isn't the above edited version a bit more like you've taken some time with your post?

Anyhow, he's just using rsync for the copy, you could use 'cp -a' .. the choice is yours.

best ...

---

### Post by qwertyjjj on 2012-02-14
> **SeijiSensei said:**
> I use rsync for most bulk copying tasks.  That command should copy the entire mysql directory from backup into /var/lib.  You can use "cp -a" if you prefer.

Ah ok, I just copied the /var/lib/mysql.
I am now trying to start mysql (sudo service mysql start) but it just seems to hang

I looked here but still can't get it to work: [http://ubuntuforums.org/showthread.php?t=1475798](http://ubuntuforums.org/showthread.php?t=1475798)
```

jack@jack-Inspiron-9300:~$ sudo nano /etc/mysql/debian.cnf
[sudo] password for jack: 
jack@jack-Inspiron-9300:~$ sudo /usr/sbin/mysqld
jack@jack-Inspiron-9300:~$ su - mysql
Password: 
su: Authentication failure
jack@jack-Inspiron-9300:~$ mysql -u root --password=password
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
jack@jack-Inspiron-9300:~$ pidof mysql
jack@jack-Inspiron-9300:~$ start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.228" (uid=1000 pid=29758 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```

```

jack@jack-Inspiron-9300:~$ ps ax | grep -i mysqld
31377 pts/0    S+     0:00 grep --color=auto -i mysqld
jack@jack-Inspiron-9300:~$ ps ax | grep -i mysql
31014 ?        S      0:00 /bin/bash /usr/bin/mysql-workbench
31019 ?        S      0:00 /bin/sh /usr/bin/catchsegv /usr/bin/mysql-workbench-bin
31021 ?        SLl    0:04 /usr/bin/mysql-workbench-bin
31385 pts/0    S+     0:00 grep --color=auto -i mysql
jack@jack-Inspiron-9300:~$ sudo service start mysql
[sudo] password for jack: 
start: unrecognized service
jack@jack-Inspiron-9300:~$ sudo service mysql start



```

```

jack@jack-Inspiron-9300:~$ mysql -u root --password=password
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
jack@jack-Inspiron-9300:~$ 

```

---

### Post by qwertyjjj on 2012-02-14
I did a reconfigure and now get this error:
Also, in my backup, the file is in /etc/mysql/my.cnf not /etc/my/cnf

What check_admin_commands/local
Checking command 'ps -C mysqld -o pid='
Server detected as running
What find_config_file/local
Check if /etc/my.cnf can be accessed
Operation failed: File /etc/my.cnf doesn't exist

---


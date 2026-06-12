---
title: "mysql 5.5.6-rc error"
date: 2010-09-26
forum: General Help
---

### Post by satish_j on 2010-09-26
getting foll error during 'make' part of compilation of mysql v5.5.6rc 
```

libtool: link: unsupported hardcode properties
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[2]: *** [mysql] Error 1
make[2]: Leaving directory `/opt/source_files/mysql-5.5.6-rc/client'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/opt/source_files/mysql-5.5.6-rc/client'
make: *** [all-recursive] Error 1

```
Any ideas how to resolve the same??

---

### Post by satish_j on 2010-09-26
well, i tried it fom scratch and the error went away,but now this new error which comes on initializing the startup tables i.e bin/mysql_install_db --user=mysql

Error is:
```

sudo bin/mysql_install_db --user=mysql
[sudo] password for satish: 
Warning: skipping '!includedir /etc/mysql/conf.d/' directive as maximum includerecursion level was reached in file /etc/mysql/conf.d/my.cnf at line 130

FATAL ERROR: Could not find mysqld

The following directories were searched:

    /usr/libexec
    /usr/sbin
    /usr/bin

If you compiled from source, you need to run 'make install' to
copy the software into the correct location ready for operation.

If you are using a binary release, you must either be at the top
level of the extracted archive, or pass the --basedir option
pointing to that location.

```
Any help now??

---

### Post by satish_j on 2010-10-01
itis now close to 15 days and still i cannot install mysql on my system.(i doubt whether it is LUcid issue as i installed it on Hardy before in the very 1st attempt,but may be iam wrong..)
i tried it from source and also from binary distribution .
It seems that the installation part is going normal(i.e i do not get any errors),but finally when i try to start the server using 'mysql -u root -p' command,iam getting the foll error:
```
The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1

```
Pls,pls,pls someone help me out OR suggest me some other forums on INternet where i can get the help on it?

---

### Post by satish_j on 2010-10-02
regretable Bump..:confused:

---

### Post by tluo on 2010-10-06
I just had MySQL 5.5.6-rc installed on Ubuntu 10.10

See this post

[http://oracleabc.com/b/archives/1866](http://oracleabc.com/b/archives/1866)

[http://oracleabc.com/b/archives/1858](http://oracleabc.com/b/archives/1858)

---

### Post by satish_j on 2010-10-07
> **tluo said:**
> I just had MySQL 5.5.6-rc installed on Ubuntu 10.10

See this post

[http://oracleabc.com/b/archives/1866](http://oracleabc.com/b/archives/1866)

[http://oracleabc.com/b/archives/1866](http://oracleabc.com/b/archives/1866)

Thanks for your reply,but my issue is different as you can see from my last post.
I an getting this message as "The package mysql can be found in following packages....." on logging in mysql using 'mysql -u root -p'

Have searched a lot on google,but still havn't got any success.
BTW,can you tell me what do you get in output when you run foll:
```

cd /usr/local/mysql/
sudo bin/mysqld_safe --user=mysql &

```

---

### Post by satish_j on 2010-10-07
I've just noticed a thing..my.cnf file is missing mysqld_safe section.can this be the cause of issue??
Can you post my.cnf file from your system?

---

### Post by tluo on 2010-10-07
I deleted the old data files and my.cnf.
mysql_install does it all.
Glad I haven't closed my terminal, here are the output of my mysql_install_db.

$sudo ./scripts/mysql_install_db --user=mysql
Installing MySQL system tables...
OK
Filling help tables...
OK

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:

./bin/mysqladmin -u root password 'new-password'
./bin/mysqladmin -u root -h ubuntu-obs password 'new-password'

Alternatively you can run:
./bin/mysql_secure_installation

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the manual for more instructions.

You can start the MySQL daemon with:
cd . ; ./bin/mysqld_safe &

You can test the MySQL daemon with mysql-test-run.pl
cd ./mysql-test ; perl mysql-test-run.pl

Please report any problems with the ./bin/mysqlbug script!


[3]   Exit 2                  ./bin/mysqld_safe
$sudo ./bin/mysqld_safe &
[3] 5656
$101006 14:49:07 mysqld_safe Logging to '/usr/local/mysql-5.5.6-rc-linux2.6-i686/data/ubuntu-obs.err'.
101006 14:49:07 mysqld_safe Starting mysqld daemon with databases from /usr/local/mysql-5.5.6-rc-linux2.6-i686/data

$

[http://oracleabc.com/b/archives/1858](http://oracleabc.com/b/archives/1858)

---

### Post by satish_j on 2010-10-08
I cannot understand where to look for solution:
Iam getting the message as "Starting mysqld daemon with databases from /usr/local/mysql-5.5.6-rc-linux2.6-i686/data",
 but on next line,if i type "mysql -u root -p":
I get message as "The package 'mysql' can be found in following packages...blah blah."
have also noticed that Telent to port 3306 cannot be established after starting mysqld_safe.
Iam going Nuts.Desperately seeking help from mysql experts..:(:(

---

### Post by satish_j on 2010-10-08
Ok,iam now asking for a working my.cnf file of mysql5.1.5 or 5.5.6
Anyone??

---

### Post by satish_j on 2010-10-15
Ok,i think i found out the problem.Client binaries needs to be installed separately after installing server.
Just a question(if anybody knows),does the tar balls downloaded from dev.mysql.com does not include Client binaries???

---


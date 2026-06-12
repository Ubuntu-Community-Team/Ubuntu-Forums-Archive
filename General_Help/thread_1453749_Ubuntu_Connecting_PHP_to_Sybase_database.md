---
title: "Ubuntu Connecting PHP to Sybase database"
date: 2010-04-13
forum: General Help
---

### Post by morgue on 2010-04-13
At work we have a Sybase Adaptiver Server 9.0 database running, it has to stay there for now, and we are developing a web application that will connect to it using PHP.

I was already able to make it work using ODBC on Windows and using odbc_connect on PHP.

But now we are moving to Ubuntu, and we are trying to get it to work on it.

I already have Apache2 and PHP5 up and running.

There are two ways (I can think of) we can do this, one is using ODBC and then use "odbc_connect" and the other is making "sybase_connect" work on PHP. Being the latter probably the best one since you wouldn't have ODBC as an intermediary.

Either way, as long as it works I'm happy. ODBC would be fine to meet our requirements for now.

I already have ODBC Data Source Administrator but no idea how to create/include/add the Sybase driver.

We also tried setting freetds up, but that didn't work either, we might be missing something.

Anyway, if anyone can help me on either department, I'd appreciate it.

---

### Post by morgue on 2010-04-13
bump

---

### Post by john newbuntu on 2010-04-14
Not sure on why you are going the odbc connect way when the Sybase CT extension has already been built in and optimized for Sybase in PHP.  Most other ways involve indirection using bridges and will generally be slower.  I have not used freetds myself but it appears to add that indirection to the DB.

If you go the sybase_connect way, you need to set up your Sybase interfaces file properly in php.ini.  And then something like this ought to do the trick for a simple connection:
```
<?
$connection = sybase_connect("servername","username","password");
```

For more details on PHP's documentation on Sybase refer:
[http://www.php.net/manual/en/book.sybase.php](http://www.php.net/manual/en/book.sybase.php)

Oh BTW, it is high time to upgrade your ASE version as it is old and unsupported.  But that's your call.

---

### Post by morgue on 2010-04-14
> **john newbuntu said:**
> Not sure on why you are going the odbc connect way when the Sybase CT extension has already been built in and optimized for Sybase in PHP.  Most other ways involve indirection using bridges and will generally be slower.  I have not used freetds myself but it appears to add that indirection to the DB.

If you go the sybase_connect way, you need to set up your Sybase interfaces file properly in php.ini.  And then something like this ought to do the trick for a simple connection:
```
<?
$connection = sybase_connect("servername","username","password");
```

For more details on PHP's documentation on Sybase refer:
[http://www.php.net/manual/en/book.sybase.php](http://www.php.net/manual/en/book.sybase.php)

Oh BTW, it is high time to upgrade your ASE version as it is old and unsupported.  But that's your call.

When I try 
[PHP]
<?php
echo sybase_connect("192.168.0.7:49152", "dba", "sql");
?>
[/PHP]

I get
```
Warning: sybase_connect() [function.sybase-connect]: message: ASA Error -83: Specified database not found (severity 16) in /home/david/public_html/sybase_test.php on line 11

Warning: sybase_connect() [function.sybase-connect]: General SQL Server error: Check messages from the SQL Server (severity 16) in /home/david/public_html/sybase_test.php on line 11

Warning: sybase_connect() [function.sybase-connect]: Unable to connect to server: 192.168.0.7:49152 in /home/david/public_html/sybase_test.php on line 11
```

I need to setup the interface file, but I really can't find good details on how to do it.

---

### Post by john newbuntu on 2010-04-14
I hope you have sybase.interface_file variable set up properly in php.ini to
point to the location of the interfaces file.  It normally points to
/usr/sybase/interfaces or whichever directory sybase has been installed in.
I also assume that based on this you have set the $SYBASE environment
variable properly (in this case to /usr/sybase)

Then edit the interfaces file to suit your needs:

```
MYSERVER
 query tcp ether 192.168.0.7 49152
 master tcp ether 192.168.0.7 49152
```Now before you even go into PHP, start your Sybase server and type the following and make sure you are able to access the Sybase database:
```
$SYBASE/bin/isql -S MYSERVER -U usr1 -P pass
```assuming 'pass' is the password for the user 'usr1'.

If that succeeds, try this in php:
<?php
echo sybase_connect("MYSERVER", "usr1", "pass");
?>

---

### Post by morgue on 2010-04-14
> **john newbuntu said:**
> I hope you have sybase.interface_file variable set up properly in php.ini to
point to the location of the interfaces file.  It normally points to
/usr/sybase/interfaces or whichever directory sybase has been installed in.
I also assume that based on this you have set the $SYBASE environment
variable properly (in this case to /usr/sybase)

Then edit the interfaces file to suit your needs:

```
MYSERVER
 query tcp ether 192.168.0.7 49152
 master tcp ether 192.168.0.7 49152
```Now before you even go into PHP, start your Sybase server and type the following and make sure you are able to access the Sybase database:
```
$SYBASE/bin/isql -S MYSERVER -U usr1 -P pass
```assuming 'pass' is the password for the user 'usr1'.

If that succeeds, try this in php:
<?php
echo sybase_connect("MYSERVER", "usr1", "pass");
?>

I forgot to mention the Sybase server is running on Windows (192.168.0.7), so I don't believe the isql command would work unless I setup something else. I don't have sybase installed on Ubuntu.

I created the interfaces file in /usr/sybase/interfaces (I created the sybase folder in there also, which wasn't present)

I executed "sudo gedit /usr/sybase/interfaces" and pasted:
```
myserver
	query tcp ether 192.168.0.7 49152
	master tcp ether 192.168.0.7 49125
```

Restarted
sudo /etc/init.d/apache2 restart

My test.php file has this
sybase_connect("myserver", "dba", "sql");

But I get
Warning: sybase_connect() [function.sybase-connect]: Unable to connect to server: myserver in /home/david/public_html/sybase_test.php on line 11

---

### Post by morgue on 2010-04-14
I'm downloading Sybase for Linux right now from
[http://www.sybase.com/linux](http://www.sybase.com/linux)

Sybase Adaptive Server Enterprise to be precise...

Taking forever... :(

---

### Post by john newbuntu on 2010-04-15
Sorry I assumed that you had ASE on Linux.  Anyways, once you install and configure it, you should have a working version of ASE and an all linux solution.

I was Googling for connecting using freetds when I found the following article.  Go through this and see if it helps you.
[http://www.linuxjournal.com/article/6636](http://www.linuxjournal.com/article/6636)

---

### Post by morgue on 2010-04-15
> **john newbuntu said:**
> Sorry I assumed that you had ASE on Linux.  Anyways, once you install and configure it, you should have a working version of ASE and an all linux solution.

I was Googling for connecting using freetds when I found the following article.  Go through this and see if it helps you.
[http://www.linuxjournal.com/article/6636](http://www.linuxjournal.com/article/6636)

Well [installing]("http://www.faqs.org/docs/Linux-mini/Sybase-PHP-Apache.html#INSTPHP") ASE was a big fail... I got multiple errors during setup when it tried to create the server and stuff.... I'll leave that for now.

For FreeTDS I was able to get the Driver
(With some help from this therad [http://ubuntuforums.org/showthread.php?t=433435&page=2](http://ubuntuforums.org/showthread.php?t=433435&page=2) since the actual driver /usr/lib/odbc/libtdsodbc.so was missing)
So I was able to create the System DSN using that driver

But on my test php file I get this
```
Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][FreeTDS][SQL Server]Unable to connect to data source, SQL state S1000 in SQLConnect in /home/david/public_html/odbc_test.php on line 3
```

File details:
**freetds.conf** (which I have in two directories because I don't know which one is the right one ([Don't quite understand this part on the FreeTDS guide]("http://www.freetds.org/userguide/freetdsconf.htm")) /etc/freetds/freetds.conf /usr/local/etc/)
```
#   $Id: freetds.conf,v 1.12 2007/12/25 06:02:36 jklowden Exp $
#
# This file is installed by FreeTDS if no file by the same 
# name is found in the installation directory.  
#
# For information about the layout of this file and its settings, 
# see the freetds.conf manpage "man freetds.conf".  

# Global settings are overridden by those in a database
# server specific section
[global]
        # TDS protocol version
;	tds version = 4.2

	# Whether to write a TDSDUMP file for diagnostic purposes
	# (setting this to /tmp is insecure on a multi-user system)
;	dump file = /tmp/freetds.log
;	debug flags = 0xffff

	# Command and connection timeouts
;	timeout = 10
;	connect timeout = 10
	
	# If you get out-of-memory errors, it may mean that your client
	# is trying to allocate a huge buffer for a TEXT field.  
	# Try setting 'text size' to a more reasonable limit 
	text size = 64512

# A typical Sybase server
[smile_odbc_ini]
	host = 192.168.0.7
	port = 49152
	tds version = 4.2


```

/etc/**odbcinst.ini**
```
[FreeTDS]
Description     	= TDS driver (Sybase/MS SQL)
Driver          	= /usr/lib/odbc/libtdsodbc.so
Setup           	= /usr/lib/odbc/libtdsS.so
CPTimeout       	=
CPReuse         	=
FileUsage       	= 1
```

/etc/**odbc.ini**
```

[ODBC Data Sources]
odbcname		= MyODBC 3.51 Driver DSN

[smile_pruebas]
Description		= CommuniCap - Dmc
Driver		= FreeTDS
Servername		= smile_odbc_ini
Database		= smile_pruebas
UID		= dba
PWD		= sql
Port		= 49152
Trace		= No

```

**odbc_test.php**
```
<?php

$conn=odbc_connect('smile_pruebas','dba','sql');

if (!$conn) {
    echo "Error en la conección.";
}
?>
```

I appreciate any suggestions.

---

### Post by morgue on 2010-04-15
I'm using TDS protocol version 4.2 
[http://www.freetds.org/userguide/choosingtdsprotocol.htm](http://www.freetds.org/userguide/choosingtdsprotocol.htm)

---

### Post by morgue on 2010-04-15
Finally got it to work... Wow!

Went through so much I really don't know what is it that made it work, but I'll try to post as many details as I can

The packages I have right now and which I believe are needed
unixodbc
unixodbc-dev
unixodbc-bin
freetds-dev
libct3
php5-odbc

I also have iodbc stuff which I'm pretty sure is not used, but just in case the packages are
iodbc
libiodbc2

Testing it with isql was as easy as running this command:
isql smile_pruebas dba sql

I'll be right back with the files, I need to clean them up a little, but wanted to post that I actually got it to work which made my happy  :guitar:

---

### Post by john newbuntu on 2010-04-16
Glad you got it to work.  But sad to note that you had ASE installation problems on Linux and therefore not an all-linux solution.

---

### Post by morgue on 2010-04-16
OK here's the file info... I removed the freetds.conf files in /home/david/ and in /usr/local/etc/, so either the [documentation]("http://www.freetds.org/userguide/freetdsconf.htm") is wrong (because it says /usr/... should be the default localtion, the install from synaptic install has changed settings*, or there is a config file or setting that I am missing.

/etc/**odbc.ini**
```

[odbc_smile_pruebas]
Description	= Servidor de Pruebas de Smile
Driver		= freetds
Servername	= smile_pruebas
;Database	= smile_pruebas
;UID		= dba
;PWD		= sql
;Port		= 49152

```
I commented some stuff, but I don't know, it might work for you...

/etc/**odbcinst.ini**
```

[freetds]
Description	= FreeTDS 0.61-5 Deb
Driver		= /usr/lib/odbc/libtdsodbc.so
Driver64	= 
Setup		= /usr/lib/odbc/libtdsS.so
Setup64		= 
UsageCount	= 
CPTimeout	= 
CPReuse		= 
FileUsage	= 1

```

/etc/freetds/**freetds.conf**
```

[smile_pruebas]
        host = 192.168.0.7
        port = 49152 
        tds version = 4.2

```

Wish I knew exactly the packages just in case so I'm not missing any, but 
it was pretty much everything related to freetds and unixodbc that made it work.

The right info on the .ini files also helped :P

I think the easiest way to test your connection is with
```
isql odbc user password
```
where odbc is the odbc.ini name between [] in my case [odbc_smile_pruebas]

or
```

<?php
odbc_connect('odbc_smile_pruebas','dba','sql');
?>

```
* It might be this, considering the libtdsodbc.so file is missing on it.

Hope someone else find this useful :)

---

### Post by morgue on 2010-04-16
> **john newbuntu said:**
> Glad you got it to work.  But sad to note that you had ASE installation problems on Linux and therefore not an all-linux solution.

Well yeah, but considering it's unixodbc, and freetds, it's OK... I might try installing ASE Linux again at some point since I already have the file in there but not for now...

:popcorn:

---

### Post by morgue on 2011-05-05
The database server has to be running as a **service** in Adaptive Server, otherwise, if it's running as an application it doesn't work.

Thought I'd add this in here since we just found out :)

---

### Post by morgue on 2011-08-25
We are moving on to using Kohana, and on the Kohana forums I asked how I'd connect using ODBC and stuff, they suggested to use PDO, so to keep this thread updated, this is how you'd connect using FreeTDS.

```

$dbh = new PDO('odbc:Driver=FreeTDS; Dsn=odbc_smile_pruebas; Uid=dbusername; Pwd=dbpassword;');

```

Still haven't managed to make Kohana connect directly.

There's very good info here as well
[http://www.phpro.org/tutorials/Introduction-to-PHP-PDO.html](http://www.phpro.org/tutorials/Introduction-to-PHP-PDO.html)

---


---
title: "Ubuntu, Lampp, Php and MS Sql Server 2008"
date: 2012-06-08
forum: General Help
---

### Post by flyns on 2012-06-08
Hello,
 
This is my first post: I'm quite new to Ubuntu. 
 
I've installed the new Ubuntu version, installed last LAMPP version, and I need to make a connection to a Microsoft SQL Server 2008, using PHP.
 
PHP commands look quite simple:
[INDENT]$connection=mssql_connect("[server]","[user]", "[password]") or die ("Can't connect");
[/INDENT]... but I just can't get connected to the server. I always get the netx message:
[INDENT]Warning: mssql_connect() [function.mssql-connect]: Unable to connect to server: [server]
Can't connect
[/INDENT]I've seen some posts on Internet blogs, forums and webs, and I've tried to follow some of the tips and recommendations I've read (modify php.ini settings, for example) , but... they didn't work at all, I always get the "Unable to connect to server" message.
 
I admit I need a step-by-step guide (for dummies), and some help. Is there anything I can follow to make sure it will work? Any advise?
 
Thanks a lot !
 
Flyns.

---

### Post by greenpeace on 2012-06-08
Hi!

First thing to check is whether you're trying to open a connection to MySQL server or to Microsoft SQL Server (which wouldn't be installed on an Ubuntu box).

So, if you are using the local MySQL server this example should help you get started!

[http://www.php.net/manual/en/mysql.examples-basic.php](http://www.php.net/manual/en/mysql.examples-basic.php)

---

### Post by flyns on 2012-06-08
Hi Greenpeace:
 
I'm trying to connect to a Microsoft SQL Server (located and running ok on another server).
 
Thanks!

---

### Post by greenpeace on 2012-06-08
ok!  thought it best to check!  :)

Is that mssql server exposed to connections from the outside?  That would be the next thing to check.  


... however do bear in mind that this may not really be the best thing from a security point of view either.

---

### Post by kanikilu on 2012-06-08
This is probably obvious, but are you sure you are using the correct server name, port, username and password in your mssql_connect function? Also, are you sure the host is setup to allow the external connection?

In the error you posted, it's unclear if you used the actual server/host name or if you literally used "[server]", which obviously won't work.

I think the default port is 1433 for mssql, but to check, nmap the host. Once you have that, in the connect string, try ```
hostname:port
```

---

### Post by flyns on 2012-06-08
Hi kanikilu,
 
I used the server ip and the name, the real answer (without "coding" it) is: 
 
**Warning**: mssql_connect() [[function.mssql-connect]("http://192.168.0.38/pruebas/function.mssql-connect")]: Unable to connect to server: 192.168.0.31\db2:1433 
 
The port is, as you said, 1433 (I verified it with nmap).
 
 
More ideas?
 
Thanks !

---

### Post by Habitual on 2012-06-08
> **flyns said:**
> ...More ideas?
 
Thanks !

Yep.
```
telnet 192.168.0.31 1433 
```

---

### Post by kanikilu on 2012-06-08
Reading through the mssql_connect() doc on php.net, it seems you are not alone in having issues connecting:

[http://php.net/manual/en/function.mssql-connect.php](http://php.net/manual/en/function.mssql-connect.php)

The first comment suggests that you don't use the "computer-name\instance-name" format on unix:

> The following method: server\instance
does'nt work on unix systems...

An instance is nothing more than specific port address different than 1433... so just discover the port on mssql server and then try to connect using:

```
ip:port
```

In unix the port is specified by : not by ,

---

### Post by flyns on 2012-06-08
> **Habitual said:**
> Yep.
```
telnet 192.168.0.31 1433 
```
 
 
 
Done!
 
That's the result:
 
[EMAIL="root@webserver:/opt/lampp/htdocs"][COLOR=black]root@webserver:/opt/lampp/htdocs[/COLOR][/EMAIL]# telnet 192.168.0.31 1433
Trying 192.168.0.31...
Connected to 192.168.0.31.
Escape character is '^]'.
 
 
It looks like it works...
 
 
Thanks!

---

### Post by Dragonbite on 2012-06-08
I had the opposite issue a couple years back.. connecting to MySQL using ASP.NET. 

Is it a full-blown SQL Server or SQL Server Express?  

In the following example I see them call the server '<servername>\SQLEXPRESS' and I don't know if 'SQLEXPRESS' is the name of their database or just the type.```

<?php
// Server in the this format: <computer>\<instance name> or 
// <server>,<port> when using a non default port number
$server = 'KALLESPC\SQLEXPRESS';

// Connect to MSSQL
$link = mssql_connect($server, 'sa', 'phpfi');

if (!$link) {
    die('Something went wrong while connecting to MSSQL');
}
?>

```
It does make me wonder, when do you specify the database to connect to? Maybe that has to be added to the server variable?

Just to make sure, did you find the documentation in the PHP Manual for Ms SQL Server ([[COLOR="Blue"]http://php.net/manual/en/book.mssql.php[/COLOR]]("http://php.net/manual/en/book.mssql.php"))

Under requirements> To use the MSSQL extension on Unix/Linux, you first need to build and install the FreeTDS library. Source code and installation instructions are available at the FreeTDS home page: » [http://www.freetds.org/](http://www.freetds.org/)

---

### Post by flyns on 2012-06-08
> **kanikilu said:**
> Reading through the mssql_connect() doc on php.net, it seems you are not alone in having issues connecting:
 
[http://php.net/manual/en/function.mssql-connect.php](http://php.net/manual/en/function.mssql-connect.php)
 
The first comment suggests that you don't use the "computer-name\instance-name" format on unix:
 
IT WORKED !!! Thanks a lot !
 
I can't believe it was that easy, I've been trying several things and it was just that ¿? Unbelievable! Let's see if I can make the entire connection... yes... omg...
 
Thanks a lot, guys!
 
(I've got new problems now! thanks!)
 
Flyns.

---

### Post by flyns on 2012-06-08
> **Dragonbite said:**
> I had the opposite issue a couple years back.. connecting to MySQL using ASP.NET. 
 
Is it a full-blown SQL Server or SQL Server Express? 
 
In the following example I see them call the server '<servername>\SQLEXPRESS' and I don't know if 'SQLEXPRESS' is the name of their database or just the type.```

<?php
// Server in the this format: <computer>\<instance name> or 
// <server>,<port> when using a non default port number
$server = 'KALLESPC\SQLEXPRESS';
 
// Connect to MSSQL
$link = mssql_connect($server, 'sa', 'phpfi');
 
if (!$link) {
    die('Something went wrong while connecting to MSSQL');
}
?>

```
It does make me wonder, when do you specify the database to connect to? Maybe that has to be added to the server variable?
 
Just to make sure, did you find the documentation in the PHP Manual for Ms SQL Server ([[COLOR=blue]http://php.net/manual/en/book.mssql.php[/COLOR]]("http://php.net/manual/en/book.mssql.php"))
 
Under requirements
 
 
Hi Dragonbite, I use MS SQL Server 2008 (not an express edition).
 
I think the database must be specified once you've made the connection, something like this:
 
$link = mssql_connect('KALLESPC', 'sa', 'phpfi');
 
mssql_select_db("SQLEXPRESS",$link);
 
(I guess Kallespc is the name of the server, and sqlexpress the name of the database).
 
 
Flyns.

---


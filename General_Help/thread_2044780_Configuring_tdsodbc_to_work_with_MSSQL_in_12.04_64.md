---
title: "Configuring tdsodbc to work with MSSQL in 12.04 64-bit"
date: 2012-08-19
forum: General Help
---

### Post by kyleboddy on 2012-08-19
I'm trying to get MSSQL working on Ubuntu 12.04 via ODBC, and I've followed these steps to the letter:

[http://jamesrossiter.wordpress.com/2011/03/08/connecting-to-microsoft-sql-server-using-odbc-from-ubuntu-server/](http://jamesrossiter.wordpress.com/2011/03/08/connecting-to-microsoft-sql-server-using-odbc-from-ubuntu-server/)

However, this omits both of these files that are pointed at in odbcinst.ini:

```
Driver = /usr/lib/odbc/libtdsodbc.so
Setup = /usr/lib/odbc/libtdsS.so
```

So, I googled a bit and found this:

[http://ubuntuforums.org/showthread.php?t=433435&page=2](http://ubuntuforums.org/showthread.php?t=433435&page=2)

So I followed those instructions and put libtdsodbc.so in /usr/lib/odbc/, but I still get this error:

```
Can't open lib '/usr/lib/odbc/libtdsodbc.so' : file not found, SQL state 01000 in SQLConnect
```

But...

```
root@ubuntu:/usr/lib/odbc# ls -la
total 552
drwxr-xr-x  2 root root   4096 Aug 19 20:12 .
drwxr-xr-x 62 root root  12288 Aug 19 19:41 ..
-rwxrwxr-x  1 root root 270608 Aug 19 20:00 libtdsodbc.so
```

I tried chmod 775 on that file, which explains the permissions. Still no luck.

Further steps I took:

I tried manually getting the 64-bit package from here:

[http://www.ubuntuupdates.org/package/core/precise/main/base/tdsodbc](http://www.ubuntuupdates.org/package/core/precise/main/base/tdsodbc)

And then I saw there was a file called this:

```
/usr/lib/x86_64-linux-gnu/odbc/libtdsodbc.so
```

Woo, maybe a 64-bit version, right?

So I pointed odbcinst.ini at it, and it didn't work.

Any help you guys can offer would be awesome. Thanks.

---

### Post by kyleboddy on 2012-08-19
Ah, progress! I found a copy of a 64-bit version of that file (I guess), and now when I run isql, I get this:

[S1000][unixODBC][FreeTDS][SQL Server]Unable to connect to data source
[01000][unixODBC][FreeTDS][SQL Server]Unknown host machine name.

odbcinst -j returns:

```
unixODBC 2.2.14
DRIVERS............: /etc/odbcinst.ini
SYSTEM DATA SOURCES: /etc/odbc.ini
FILE DATA SOURCES..: /etc/ODBCDataSources
USER DATA SOURCES..: /home/kyle/.odbc.ini
SQLULEN Size.......: 8
SQLLEN Size........: 8
SQLSETPOSIROW Size.: 8

```

odbcinst.ini:

```
[FreeTDS]
Description = TDS driver (Sybase/MS SQL)
# Driver = /usr/lib/libtdsodbc.so
Driver = /usr/lib/x86_64-linux-gnu/odbc/libtdsodbc.so
Setup = /usr/lib/odbc/libtdsS.so
CPTimeout =
CPReuse =
FileUsage = 1
```

odbc.ini:

```
[blahblah]
Driver = FreeTDS
Description  = ODBC connection via FreeTDS
Trace = No
Servername = servernameredacted
Database = TestDB
```

Command I'm running:

```
isql -v blahblah username password
```

---


---
title: "Connect to MySQL on ubuntu using VB6 application"
date: 2010-10-26
forum: General Help
---

### Post by dvmurray on 2010-10-26
Hi,

I am looking for some advice on the best way to connect to a MySQL database on a Ubuntu server via SSH.  The application is built using VB6 and is installed on a Windows server.  

Any thoughts would be much appreciated.

Thanks from a newbie.

David

---

### Post by DaithiF on 2010-10-26
Hi, there are a few elements to this ..

1. Download & install the mysql odbc driver for windows:
[http://dev.mysql.com/downloads/connector/odbc/5.1.html](http://dev.mysql.com/downloads/connector/odbc/5.1.html)

2. Set up a ssh tunnel from a particular port on your client machine to the mysql port on the ubuntu machine.  This reference may be useful (uses Cygwin ssh):
[http://www.murdoch-sutherland.com/mysql.html](http://www.murdoch-sutherland.com/mysql.html)
or this is another one using a different ssh client:
[http://lists.mysql.com/myodbc/15](http://lists.mysql.com/myodbc/15)

3. Connect in VB using the appropriate ConnectionString ... i'm very rusty on VB so this may be out of date, but something like:
```
dim objConn as Adodb.Connection, strConn as string
strConn = ""DRIVER={MySQL ODBC 3.51 Driver};\
                   SERVER=localhost;\
                   PORT=3307;\
                   DATABASE=dbname;\
                   USER=username;\
                   PASSWORD=password;"
objConn.Open ConnectionString:=strConn
```
Note the driver name will depend on whatever version you download in step 1, and port will depend on how you set up the tunnel

---

### Post by dvmurray on 2010-10-27
Thank you DaithiF.  I'll give it go and let you know how I get on.

---


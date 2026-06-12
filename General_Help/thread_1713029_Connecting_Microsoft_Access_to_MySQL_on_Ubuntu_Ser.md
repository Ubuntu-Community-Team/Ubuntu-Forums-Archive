---
title: "Connecting Microsoft Access to MySQL on Ubuntu Server"
date: 2011-03-23
forum: General Help
---

### Post by dawbomb on 2011-03-23
Hi All,

I've been using ubuntu for quite a few years, and know the basics of databases.  However, how to get them to talk to each other...  Not so much.

I need to be able to connect to a MySQL database using Microsoft Access 20074.  The database is going to be running on my server, which runs ubuntu server 10.10.

So far, I have installed MySQL server and libmyodbc.  I took the deetails for the odbc.ini file from the ODBC ubuntu community page, so this is the current setup (database name is business):

```

[ODBC Data Sources]
odbcname     = MyODBC 3.51 Driver DSN

[business]
Driver       = /usr/lib/odbc/libmyodbc.so
Description  = MyODBC 3.51 Driver DSN
SERVER       = localhost
PORT         =
USER         = businessuser
Password     = <password>
Database     = business
OPTION       = 3
SOCKET       =

[Default]
Driver       = /usr/lib/odbc/libmyodbc.so
Description  = MyODBC 3.51 Driver DSN
SERVER       = localhost
PORT         =
USER         = root
Password     =
Database     = test
OPTION       = 3
SOCKET       =

```

Can anybody please help me get this working?  When I try to connect using Access, I get "Server does not exist or access denied."

Thanks in advance!

---

### Post by lykwydchykyn on 2011-03-23
I don't think you need odbc on the server, more likely what you need is to install the MySQL connector driver on your Windows workstation that's running Access.  Then you can set up an ODBC connection to the server.

You can get the connector here:  [http://www.mysql.com/products/connector/](http://www.mysql.com/products/connector/)

---

### Post by wyliecoyoteuk on 2011-03-23
You will need to add it in the data sources in control panel on the windows box.

---

### Post by dawbomb on 2011-04-23
> **lykwydchykyn said:**
> I don't think you need odbc on the server, more likely what you need is to install the MySQL connector driver on your Windows workstation that's running Access.  Then you can set up an ODBC connection to the server.

You can get the connector here:  [http://www.mysql.com/products/connector/](http://www.mysql.com/products/connector/)

Brilliant, thanks so much!  Worked like a charm!

---


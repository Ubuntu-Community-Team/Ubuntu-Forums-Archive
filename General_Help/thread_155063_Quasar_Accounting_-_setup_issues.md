---
title: "Quasar Accounting - setup issues"
date: 2006-04-04
forum: General Help
---

### Post by BrownieMan on 2006-04-04
I have managed to install Quasar using this guide

[http://ubuntuforums.org/showthread.php?t=53388&highlight=quasar](http://ubuntuforums.org/showthread.php?t=53388&highlight=quasar)

but I can't get the MySQL database to work with it. Everythign is going okay until I get to step 5. In my driver's tab there is nothign to select and hitting configure says "no driver selected".  So i went to Quasar Admin and tried doing something there. When I try to to connect to my server on my computer (I'm assuming that it's installed when you install ubuntu or wahtever) it says it doesnt exist. The name has oto be right because the only other possible name I already tried.

Any ideas?

---

### Post by NewbieNik on 2006-04-04
I have no real knowledge on MySQL, but I have come across this elsewhere. You need to have the MySQL connector configured to point to the database and table you want for the data to be applied.
[www.mysql.com](www.mysql.com) has many document relating to this.

---

### Post by NewbieNik on 2006-04-04
you need to edit the odbcinst.ini to:-
[MySQL]Description = ODBC Driver for MySQL
Driver = /usr/lib/odbc/libmyodbc.so
Setup = /usr/lib/odbc/libodbcmyS.so
FileUsate = 1
CPTimeout =
CPReuse = 

then edit odbc.ini for each named connection
[*connection-name*]
Description = *whatever-you-want-it-called*
Driver = MySQL
Server = *server-name*
Database = *db-name*
Port = 3306
Socket = *socketnumber*
Option = 
Stmt =

Then you should be able to pick the driver up

---

### Post by BrownieMan on 2006-04-04
I THINK I know the server name but have no clue what my database name, or socket number should be

[QUOTE=NewbieNik]
then edit odbc.ini for each named connection
[*connection-name*]
Description = *whatever-you-want-it-called*
Driver = MySQL
Server = *server-name*
Database = *db-name*
Port = 3306
Socket = *socketnumber*
Option = 
Stmt =

Then you should be able to pick the driver up[/QUOTE]

---

### Post by NewbieNik on 2006-04-04
Without reading the Quasar docs I cannot tell you the db name, but the socket number can and usually is left blank.
Try adding MySQLAdmin in your packages and connecting to the server. This should give you the ability to manipulate the DB users and tables, but would recommend reading, thoroughly, any documents you can find before making changes! (A voice of experience in screwing up a long-winded db)

---

### Post by BrownieMan on 2006-04-04
When I enter the correct name of the server in Quasar Admin I get a unique error message: "Connection refused: This usualy means that the Quasar program is not running on the server name you entered." This is the onyl server I have, it's just one computer. I have the program installed,  how else could I open the Quasar. So I'm kinda confused as to what the problem is, any ideas?

---


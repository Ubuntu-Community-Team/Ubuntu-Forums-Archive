---
title: "Cannot connect to port 3306 (MySQL)"
date: 2010-05-08
forum: General Help
---

### Post by BruceRowe on 2010-05-08
This is a new installation of 10.04 Server. I need to connect to MySQL from the other computers on my network. But, port 3306 does not respond. I can connect through port 80 (with a browser) just fine. 

When I try the Telnet command:[INDENT][FONT=System]telnet 10.1.10.180 3306[/FONT]
[/INDENT]I get[INDENT][FONT=System]Could not open a connection to host on port 3306. Connect failed.[/FONT]
[/INDENT]Does anyone know how to start troubleshooting this problem?

Thanks in advance.

Bruce

---

### Post by sir_nasty on 2010-05-08
does this help at all?

[http://www.linuxquestions.org/questions/linux-networking-3/mysqld-running-and-reading-for-connections-on-port-3306-no-port-3306-found-from-scan-364970/](http://www.linuxquestions.org/questions/linux-networking-3/mysqld-running-and-reading-for-connections-on-port-3306-no-port-3306-found-from-scan-364970/)

---

### Post by catnap on 2010-05-23
I overwrote my mysql config file while doing a Lucid upgrade and  found the solution was to change the bind-address in /etc/mysql/my.conf
from 127.0.0.1 to the server address. 

After that I guess it makes sense to ensure that 3306 is available to the outside world, but it was in my case.

Best of luck

---


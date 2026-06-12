---
title: "How to Start ProFTPd?"
date: 2009-07-07
forum: General Help
---

### Post by antdgar on 2009-07-07
I installed it using the GUI  typing: proftpd in terminal yields this:  ```
 proftpd  - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied  - notice: unable to listen to local socket: Operation not permitted  - Fatal: SystemLog: unable to redirect logging to '/var/log/proftpd/proftpd.log': Permission denied on line 90 of '/etc/proftpd/proftpd.conf'
```     Starting the server says this ```
 sudo /etc/init.d/proftpd start ProFTPd is started from inetd/xinetd.
```  But how to really start it? So I can see the UI and create users etc?  Please help!

---

### Post by michy99 on 2009-07-07
Maybe this guide will be of some help.```
http://www.ubuntugeek.com/setting-up-a-proftp-server.html#more-1482
```

---

### Post by danwood76 on 2009-07-07
The first command gave error as the service needs to be started as root and can be done so through the GUI.

Install the GA-ADMIN for proftpd and open it up.
You need to set basic settings before you are able use the FTP daemon.

---


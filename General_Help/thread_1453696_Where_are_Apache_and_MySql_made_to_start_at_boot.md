---
title: "Where are Apache and MySql made to start at boot?"
date: 2010-04-13
forum: General Help
---

### Post by davidpbrown on 2010-04-13
Apache and MySql used to run every session but now [something changed in the last few days]("http://ubuntuforums.org/showthread.php?t=1453560") that the servers aren't running directly and I need to start them.

Obviously, I could put them in the startup programs but that seems an odd thing to do where they were restarting before.

---

### Post by sandyd on 2010-04-13
> **davidpbrown said:**
> Apache and MySql used to run every session but now [something changed in the last few days]("http://ubuntuforums.org/showthread.php?t=1453560") that the servers aren't running directly and I need to start them.

Obviously, I could put them in the startup programs but that seems an odd thing to do where they were restarting before.
Apache: ```
/etc/init.d/apache2 restart

```
MySQL:```
/etc/init.d/mysql-server
```

---

### Post by davidpbrown on 2010-04-13
Maybe it's a deamon mysql rather than a true server then..

Eitherway, using 
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart

works to fix it temporarily but then its state is not remembered, where previously it would be retained from one session to the next. I rebooted just now and it's stalled needing restart.


So, where can I put these instructions so they are called at login; is there a standard login shell script that calls services?

---

### Post by sandyd on 2010-04-13
> **davidpbrown said:**
> Maybe it's a deamon mysql rather than a true server then..

Eitherway, using 
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart

works to fix it temporarily but then its state is not remembered, where previously it would be retained from one session to the next. I rebooted just now and it's stalled needing restart.


So, where can I put these instructions so they are called at login; is there a standard login shell script that calls services?

thtas why i was a little curious

ubuntu runs everything in /etc/init.d
while starting up...

try adding it to /etc/rc.local
in the format
```

/bin/bash -c /etc/init.d/apache2/restart
```

---

### Post by davidpbrown on 2010-04-14
Adding to /etc/rc.local didn't work!?
```
/bin/bash -c /etc/init.d/apache2\ restart
/bin/bash -c /etc/init.d/mysql\ restart
```

That was a surprise, as I thought it would be essentially the same as manually doing it in the terminal.


In passing I fixed the ServerName localhost in /etc/apache2/httpd.conf which has been on my to do list forever.


What's odd is that it's both Apache and MySql.. and I don't know what other services aren't running now that should be. I can't see anything else is affected.

---

### Post by FiReiSFuN on 2010-04-14
Try:

sudo update-rc.d -f apache2 remove
sudo update-rc.d apache2 defaults

sudo update-rc.d -f mysql remove
sudo update-rc.d mysql defaults

Which will first remove all startup links to the server and then second restore the defaults (i.e. same as were made when the program was installed).

---

### Post by davidpbrown on 2010-04-14
No, it worked smoothly but no change.

---

### Post by Monotoko on 2010-04-14
I can only assume something is going wrong whilst starting them to begin with, have you checked /var/logs ?

---

### Post by davidpbrown on 2010-04-14
There's nothing there expect the ./apache2/error.log noting pairs of [resuming normal operations] and [shutting down] as I restart and reboot.


They start no problem from terminal and it's the starting them automatically that's playing up.


Worst case I'll likely be upgrading to Lucid end of month.

---

### Post by davidpbrown on 2010-04-16
This problem just appeared on my laptop too.

The only change was a security upgrade to
libpq5 (8.4.2-0ubuntu9.10) to 8.4.3-0ubuntu9.10

How that upgrade has affected localhost access and startup of Apache and MySql isn't clear to me.

---

### Post by davidpbrown on 2010-04-16
Upgrade to 10.4 appears to fix this.

---


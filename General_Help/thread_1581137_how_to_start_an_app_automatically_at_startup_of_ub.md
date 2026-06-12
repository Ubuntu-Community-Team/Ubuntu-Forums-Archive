---
title: "how to start an app automatically at startup of ubuntu"
date: 2010-09-24
forum: General Help
---

### Post by fabianus on 2010-09-24
Hello all !

I want ubuntu (10.04 server) to start openerp at startup of the server automatically. Where do I have to place this command in order to make it run ?

exec openerp-server --db_user=openuser --db_password=xxxx --logfile=/var/log/openerp-server.log --log-level=error

Thanks a lot for any help !

Best regards, 
Fabianus

---

### Post by searchfgold6789 on 2010-09-24
There is a program in the ubuntu menu for startup applications. You can have the option to have it run a custom command, I think.

---

### Post by Cavsfan on 2010-09-24
System > Preferences > Startup Applications

---

### Post by fabianus on 2010-09-25
hello guys !

Thanks for your responses !

I do not use the graphical interface. I suppose that I have to place this in a file somewhere in /etc/init but it doesn't work :-(

exec openerp-server --db_user=openuser --db_password=xxxx --logfile=/var/log/openerp-server.log --log-level=error

Thanks a lot for any further suggestions !

Best regards, 
Fabianus

---


---
title: "Setup website in Apache2 issue"
date: 2010-02-22
forum: General Help
---

### Post by daniel50096230 on 2010-02-22
I get this error when I trying to restart my Apache2, what's wrong with it?


support@ippbx:/etc/apache2/sites-enabled$ sudo /etc/init.d/apache2 restart * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs



Can anyone provide some guideline on how to configure a website in Apache in order to be browse on Internet? (Notes: I has public ip address on hand, but not sure how to configure my website to be browse by public user.)

I would be appreciate if anyone can provide the steps on configure the above setting because I am totally new to Ubuntu and Apache as well.

---

### Post by serafim on 2010-04-27
look for other program that might use port 80.
On Unix/Linux lsof -i :80 ought to give a listing
containing lines like
COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2  1966     root    4u  IPv6  47352      0t0  TCP *:www (LISTEN)
apache2  2960 www-data    4u  IPv6  47352      0t0  TCP *:www (LISTEN)

The above listing is normal but if some other program is using port 80
that programs name will be found in the COMMAND column. Then stop that program and change its configuration. Restart first Apache and then the other program.

If you cannot find any program using port 80 then Apache might be in conflict with itself. Or, rather the apache main process might be in conflict with childprocesses or with processes started as virtual servers.

Go through the conf files and see if there are multiple
Listen 80

Last time I encountered the problem I found multiple Listen directives in the conf files specifying the virtual servers

In ports.conf I found the directive and also in
sites-available/default. I commented out the directive in all files except ports.conf and everything works.

This goes even for ssl (port 443)

---


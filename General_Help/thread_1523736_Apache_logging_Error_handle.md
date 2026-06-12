---
title: "Apache logging Error handle"
date: 2010-07-04
forum: General Help
---

### Post by toledot on 2010-07-04
hello, I am new beginner in Ubuntu from Germany. 
I use ubuntu9.10 and Apache web server 2.2, after I configured some Name-based Virtual hosts on localhost, I got the following log info in /var/log/apache2/error.log
-------------------------------

[Sun Jul 04 10:58:52 2010] [notice] SIGHUP received.  Attempting to restart
[Sun Jul 04 10:58:52 2010] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Sun Jul 04 10:58:52 2010] [notice] Apache/2.2.12 (Ubuntu) DAV/2 PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g configured -- resuming normal operations
-------------------------------
what do they mean, the three errors? and can I fixed them?

regards

---

### Post by dapperdanny77 on 2010-07-04
[Sun Jul 04 10:58:52 2010] [notice] SIGHUP received.  Attempting to  restart
- it seems you did a apach2ctl restart or restart apache or /etc/init.d/apache restart - it's normal behaviour


[Sun Jul 04 10:58:52 2010] [warn] Init: Name-based SSL virtual hosts  only work for clients with TLS server name indication support (RFC 4366)
- this tells you that your name based virtual ssl hosts are only reachable from clients capable to do that - practically this means that only ancient clients are unable to connect - that's ok


[Sun Jul 04 10:58:52 2010] [notice] Apache/2.2.12 (Ubuntu) DAV/2  PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_ssl/2.2.12 OpenSSL/0.9.8g  configured -- resuming normal operations
- standard apache startup log entry - just shows you some version/module information  - that's ok 

greetings to germany - congratulations for your world cup victory against argentinia - impressing

---


---
title: "lighttpd not working"
date: 2010-06-27
forum: General Help
---

### Post by walterbyrd on 2010-06-27
I am trying to follow this tutorial:

[http://amselgrunwald.wordpress.com/2010/05/01/how-to-install-lighttpd-mysql-phpmyadmin-and-php5-on-ubuntu-10-04/](http://amselgrunwald.wordpress.com/2010/05/01/how-to-install-lighttpd-mysql-phpmyadmin-and-php5-on-ubuntu-10-04/)

Everything goes well until this point:

8 : Enable FastCGI in Lighttpd
    lighttpd-enable-mod fastcgi

> 
# lighttpd-enable-mod fastcgi
Available modules: auth cgi fastcgi proxy rrdtool simple-vhost ssi ssl status userdir 
Already enabled modules: fastcgi 
Enabling fastcgi: already enabled
Run /etc/init.d/lighttpd force-reload to enable changes
# /etc/init.d/lighttpd force-reload
Duplicate config variable in conditional 0 global: fastcgi.server
2010-06-27 13:00:50: (configfile.c.907) source: /etc/lighttpd/lighttpd.conf line: 217 pos: 1 parser failed somehow near here: (EOL) 


I do not have a line 217, the last line in the file is 216. Here is line 213 - 216:

> 
fastcgi.server = ( ".php" => ((
                     "bin-path" => "/usr/bin/php5-cgi",
                     "socket" => "/tmp/php.socket"
                 )))


Any help appreciated. Thanks in advance.

---


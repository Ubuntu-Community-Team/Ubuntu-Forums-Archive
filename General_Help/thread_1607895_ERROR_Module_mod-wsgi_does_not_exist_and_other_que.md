---
title: "ERROR: Module mod-wsgi does not exist and other questions."
date: 2010-10-28
forum: General Help
---

### Post by SpotTheWonderDog on 2010-10-28
Why am I getting this error: [SIZE=2]ERROR: Module mod-wsgi does not exist!
[/SIZE]
[SIZE=2][COLOR=Black]$ sudo a2enmod mod-wsgi
```
[COLOR=Red]ERROR: Module mod-wsgi does not exist![/COLOR]
```[/COLOR][/SIZE]

$ sudo a2enmod mod_wsgi

```
ERROR: Module mod_wsgi does not exist!
```$ a2enmod

```
Which module(s) do you want to enable (wildcards ok)?
mod*
ERROR: No module found matching mod*!
```Here are the details of what's installed and the contents of all the relevant files that I could think of:

$ locate mod_wsgi

```
/usr/lib/apache2/modules/mod_wsgi.so
/usr/lib/apache2/modules/mod_wsgi.so-2.6

``````
Apache version:  2.2.14-5ubuntu8.2
Size:            6767 kb
``````
using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013
``````

python --version
Python 2.6.5

```$ sudo service apache2 start

```
 * Starting web server apache2                                                        
 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```$ netstat -an | grep 80

```
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN

```$ dpkg -l libapache2-mod-wsgi

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libapache2-mod 2.8-2ubuntu1   Python WSGI adapter module for Apache
```$ cat /etc/apache2/mods-available/wsgi.load

```
LoadModule wsgi_module /usr/lib/apache2/modules/mod_wsgi.so
```$ apache2ctl -t -D DUMP_MODULES

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 python_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
[COLOR=Olive] wsgi_module (shared)[/COLOR]
Syntax OK
```/etc/apache2/mods-available/

```
-rw-r--r-- 1 root root 2953 2010-04-27 00:32 wsgi.conf
-rw-r--r-- 1 root root   60 2010-04-27 00:32 wsgi.load
```/etc/apache2/mods-enabled/

```
lrwxrwxrwx 1 root root 27 2010-10-26 15:29 wsgi.conf -> ../mods-available/wsgi.conf
lrwxrwxrwx 1 root root 27 2010-10-26 15:29 wsgi.load -> ../mods-available/wsgi.load

```$ dpkg -l libapache2-mod-wsgi

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libapache2-mod 2.8-2ubuntu1   Python WSGI adapter module for Apache
```$ dpkg -s libapache2-mod-wsgi

 ```

Package: libapache2-mod-wsgi
Status: install ok installed
Priority: optional
Section: httpd
Installed-Size: 220
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mod-wsgi
Version: 2.8-2ubuntu1
Depends: apache2, apache2.2-common, libc6 (>= 2.4), libpython2.6 (>= 2.6), python (>= 2.6), python (<< 2.7)
Suggests: apache2-mpm-worker | apache2-mpm-event
Conffiles:
 /etc/apache2/mods-available/wsgi.load 06d2b4d2c95b28720f324bd650b7cbd6
 /etc/apache2/mods-available/wsgi.conf 408487581dfe024e8475d2fbf993a15c
Description: Python WSGI adapter module for Apache
 The mod_wsgi adapter is an Apache module that provides a WSGI (Web Server
 Gateway Interface, a standard interface between web server software and
 web applications written in Python) compliant interface for hosting Python
 based web applications within Apache. The adapter provides significantly
 better performance than using existing WSGI adapters for mod_python or CGI.
Homepage: http://www.modwsgi.org/
Original-Maintainer: Debian Python Modules Team <python-modules-team@lists.alioth.debian.org>

```$ cat /var/log/apache2/error.log

```
[Sun Oct 24 10:02:29 2010] [notice] mod_python: Creating 8 session mutexes based on 3 max processes and 25 max threads.
[Sun Oct 24 10:02:29 2010] [notice] mod_python: using mutex_directory /tmp
[Sun Oct 24 10:02:29 2010] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 configured -- resuming normal operations
[Tue Oct 26 15:29:29 2010] [notice] caught SIGTERM, shutting down
[Tue Oct 26 15:29:30 2010] [notice] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Tue Oct 26 15:29:30 2010] [notice] mod_python: using mutex_directory /tmp
[Tue Oct 26 15:29:30 2010] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 mod_wsgi/2.8 configured -- resuming normal operations
[Tue Oct 26 16:22:40 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Tue Oct 26 16:22:43 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Oct 27 06:47:07 2010] [notice] SIGUSR1 received.  Doing graceful restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Oct 27 06:47:07 2010] [notice] mod_python: Creating 8 session mutexes based on 3 max processes and 25 max threads.
[Wed Oct 27 06:47:07 2010] [notice] mod_python: using mutex_directory /tmp
[Wed Oct 27 06:47:07 2010] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 mod_wsgi/2.8 configured -- resuming normal operations
[Wed Oct 27 17:03:04 2010] [notice] caught SIGTERM, shutting down
[Wed Oct 27 18:24:33 2010] [notice] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Wed Oct 27 18:24:33 2010] [notice] mod_python: using mutex_directory /tmp
[Wed Oct 27 18:24:33 2010] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 mod_wsgi/2.8 configured -- resuming normal operations
[Wed Oct 27 18:39:14 2010] [notice] caught SIGTERM, shutting down
[Wed Oct 27 18:39:15 2010] [notice] mod_python: Creating 8 session mutexes based on 6 max processes and 25 max threads.
[Wed Oct 27 18:39:15 2010] [notice] mod_python: using mutex_directory /tmp
[Wed Oct 27 18:39:15 2010] [notice] Apache/2.2.14 (Ubuntu) mod_python/3.3.1 Python/2.6.5 mod_wsgi/2.8 configured -- resuming normal operations
```$ cat /etc/apache2/sites-available/default

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www

    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>

    <Directory /var/www/>
      Options Indexes FollowSymLinks MultiViews ExecCGI

      AddHandler cgi-script .cgi
      AddHandler wsgi-script .wsgi

      AllowOverride None
      Order allow,deny
      allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```$ cat /etc/apache2/mods-enabled/dir.conf

```
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.code index.xhtml index.htm index.wsgi
</IfModule>
```

---

### Post by simoes94 on 2011-03-03
Spot - 

You may want to try the following:

```

sudo apt-get purge libapache2-mod-wsgi
sudo apt-get install libapache2-mod-wsgi

```As prescribed in the [following article]("http://mark.hungrybugger.co.uk/?p=447").

---


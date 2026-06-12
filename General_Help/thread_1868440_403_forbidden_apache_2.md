---
title: "403 forbidden apache 2"
date: 2011-10-24
forum: General Help
---

### Post by jas1291 on 2011-10-24
i get the following error message on my browser
Forbidden

You don't have permission to access /index.html on this server.

Apache/2.2.14 (Ubuntu) Server at [www.example.local](www.example.local) Port 80

the following is my code in /etc/apache2/sites-available/example.local file
```

<VirtualHost example.local:80>
ServerName example.local
ServerAlias www.example.local
DocumentRoot /home/jasleen/public_html

</VirtualHost>

```

the following is my error log
```
Sun Oct 23 12:34:08 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Sun Oct 23 12:34:08 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Sun Oct 23 12:34:08 2011] [notice] Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 configured -- resuming normal operations
[Sun Oct 23 12:41:31 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 13:06:13 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 13:07:02 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 15:30:01 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 15:30:16 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 15:38:21 2011] [notice] caught SIGTERM, shutting down
[Sun Oct 23 16:47:11 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Sun Oct 23 16:47:11 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Sun Oct 23 16:47:11 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Sun Oct 23 16:47:11 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Sun Oct 23 16:47:11 2011] [notice] Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 configured -- resuming normal operations
[Sun Oct 23 17:49:50 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 17:52:18 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/scrape
[Sun Oct 23 19:42:56 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 19:47:04 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 21:23:36 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 21:26:02 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 21:43:34 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 21:57:31 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 23:09:19 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Sun Oct 23 23:09:58 2011] [notice] caught SIGTERM, shutting down
[Mon Oct 24 17:29:38 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Mon Oct 24 17:29:38 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Mon Oct 24 17:29:39 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Mon Oct 24 17:29:39 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Mon Oct 24 17:29:39 2011] [notice] Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 configured -- resuming normal operations
[Mon Oct 24 17:29:57 2011] [notice] caught SIGTERM, shutting down
[Mon Oct 24 17:40:36 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Mon Oct 24 17:40:36 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Mon Oct 24 17:40:36 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Mon Oct 24 17:40:36 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Mon Oct 24 17:40:36 2011] [notice] Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 configured -- resuming normal operations
[Mon Oct 24 17:41:24 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/announce
[Mon Oct 24 18:20:53 2011] [notice] SIGUSR1 received.  Doing graceful restart
[Mon Oct 24 18:20:53 2011] [warn] No JkLogFile defined in httpd.conf. Using default /var/log/apache2/mod_jk.log
[Mon Oct 24 18:20:53 2011] [warn] No JkShmFile defined in httpd.conf. Using default /var/log/apache2/jk-runtime-status
[Mon Oct 24 18:20:53 2011] [notice] Apache/2.2.14 (Ubuntu) mod_jk/1.2.28 configured -- resuming normal operations
[Mon Oct 24 18:21:53 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:21:59 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/js.html, referer: http://www.example.local/
[Mon Oct 24 18:21:59 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:22:02 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:22:13 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/js.html
[Mon Oct 24 18:22:13 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:22:22 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:22:52 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/js.html, referer: http://www.example.local/
[Mon Oct 24 18:22:52 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:24:28 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:24:30 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:24:30 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:24:33 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:28:23 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:28:24 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:28:25 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:28:25 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:32:33 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:36:36 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:36:36 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:40:09 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:40:09 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:40:35 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:40:35 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
[Mon Oct 24 18:44:45 2011] [error] [client 127.0.0.1] (13)Permission denied: file permissions deny server access: /home/jasleen/public_html/index.html
[Mon Oct 24 18:44:45 2011] [error] [client 127.0.0.1] File does not exist: /home/jasleen/public_html/favicon.ico
```

following is my httpd.conf file
```
userdir public_html 
Options +Indexes 
Options All 

ServerName localhost 

<Directory "/home/jasleen/public_html/"> 
Options Indexes FollowSymLinks
Order allow,deny 
Allow from all 
AllowOverride All 
</Directory> 
```
what is wrong????

---

### Post by linuxwin2 on 2011-10-24
Put the output of this
```
$ls -l /home/jasleen/public_html

```
Because apache webserver use :
www-data as user and
www-data as group

---

### Post by jas1291 on 2011-10-24
total 4
-rw------- 1 jasleen jasleen 772 2011-10-10 23:35 index.html

---

### Post by linuxwin2 on 2011-10-25
with -rw------- apache server haven't access to this page
try
```
$ chmod o+r /home/jasleen/public_html/index.html

```

---


---
title: "Zend Server / Apache issues"
date: 2011-11-14
forum: General Help
---

### Post by sanukcm on 2011-11-14
Hi all. Having a problem getting my development server up and running. I have made no changes to any configs or anything, was working fine yesterday when I went home from work. 

```
root@machinename:~$ /etc/init.d/zend-server restart
Restarting Zend Server 5.5.0 ..

Stopping web server: apache2Warning: DocumentRoot [/www/sitedirectory/htdocs/] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.555 for ServerName
.
Stopping Zend Server GUI [Lighttpd] [OK]
Starting web server: apache2Warning: DocumentRoot [/www/sitedirectory/htdocs/] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.555 for ServerName
Action 'start' failed.
The Apache error log may have more information.
 failed!
spawn-fcgi: child spawned successfully: PID: 1775
Starting Zend Server GUI [Lighttpd] [OK]
[14.11.2011 06:42:10 SYSTEM] watchdog for lighttpd is running. 
[14.11.2011 06:42:10 SYSTEM] lighttpd is running. 

Zend Server started...
```

A look at the error log reveals: 


```
root@machinename:~$ tail /var/log/apache2/error.log
(2)No such file or directory: apache2: could not open error log file /var/www/logs/apache2/sitedirectory/error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /var/www/logs/apache2/sitedirectory/error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /var/www/logs/apache2/sitedirectory/error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /var/www/logs/apache2/sitedirectory/error_log.
Unable to open logs
```

Not sure what i've done to cause a problem, or where I should look to apply a solution from here. Any help is much appreciated!

---

### Post by sanukcm on 2011-11-14
I fixed it... 

we use a custom .conf / vhost file on our projects and I accidentally hosed mine by copying over a workmates custom conf file during a botched git merge at the end of the workday yesterday. [-X


Changed that file to look like this: 

```
<VirtualHost *:80>
        ServerName server.name
 
        DocumentRoot /www/sitedirectory/htdocs/
 
        ErrorLog /var/www/sitedirectory/logs/error_log
        CustomLog /var/www/sitedirectory/logs/access_log combined
        php_value error_log var/www/sitedirectory/logs/phperror_log
 
	#php_value date.timezone UTC
	php_value mbstring.language Neutral
	php_value mbstring.internal_encoding UTF-8
	php_value mbstring.encoding_translation On
	php_value mbstring.http_input auto
	php_value mbstring.http_output UTF-8
	php_value mbstring.detect_order auto
	php_value mbstring.substitute_character none
	php_value default_charset UTF-8
	

        <Directory "/www/sitedirectory/htdocs/">
                Options -Indexes FollowSymLinks
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>

</VirtualHost>
```

Which reflects where my logs actually live! Thanks!

---

### Post by linuxwin2 on 2011-11-14
Good, please mark this thread are SOLVED in title.

---


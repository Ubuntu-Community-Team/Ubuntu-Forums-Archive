---
title: "Apache2 not working right"
date: 2012-04-27
forum: General Help
---

### Post by mvmacd on 2012-04-27
Edit: 
I figured it out, I had to add this to ports.conf:
```
NameVirtualHost *:8080
Listen 8080

```
----

This is the contents of /etc/apache2/sites-available/desktop:
```


<VirtualHost *:8080>
	ServerAdmin webmaster@localhost

	DocumentRoot /8080
	<Directory /8080>
		Options FollowSymLinks
		AllowOverride all
	</Directory>
	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```
and it is enabled:
```

# ls -l /etc/apache2/sites-enabled/
total 0
lrwxrwxrwx 1 root root 26 Apr 27 12:11 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 26 Apr 27 12:43 desktop -> ../sites-available/desktop

```
and this is httpd.conf:
```

ServerName localhost

```
 I have restarted apache2, and when I try localhost:8080, it says connection refused:
```


$ curl -vI localhost:8080
* About to connect() to localhost port 8080 (#0)
*   Trying 127.0.0.1... Connection refused
* couldn't connect to host
* Closing connection #0
curl: (7) couldn't connect to host

```

anyone know what's going on?

---


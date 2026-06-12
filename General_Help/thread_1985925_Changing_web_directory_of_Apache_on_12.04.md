---
title: "Changing web directory of Apache on 12.04"
date: 2012-05-24
forum: General Help
---

### Post by jcobban on 2012-05-24
I am trying to change the web directory for Apache to point at /home/userid/public_html.  I updated /etc/apache2/sites-enabled/000-default to:


```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/jcobban/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/jcobban/public_html/>
		Options Indexes FollowSymLinks MultiViews
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

I tried "service httpd restart" but as mentioned on another thread this generates an error I do not know how to fix.  I rebooted by system instead.  When I browse to "localhost" I still get the output from /var/www/index.html.

I am not an Apache guru and I have no interest whatsoever in becoming one.  I am trying to do web development and at the moment Apache is being an obstacle to that end.

---

### Post by maverickaddicted on 2012-05-24
Try to configure the default site again. First deactivate the default site and then edit the default site file by going in /etc/apache2/sites-available/ directory. After editing it activate the site again and restart the apache service again. You default apache directory should get change.

---

### Post by jcobban on 2012-05-24
Thank you.  It works now.:KS

---

### Post by maverickaddicted on 2012-05-24
Good to hear that. You might be also interested in this -

[http://www.matthewwittering.co.uk/blog/ubuntu-tips/apache-per-user-web-directories.htm](http://www.matthewwittering.co.uk/blog/ubuntu-tips/apache-per-user-web-directories.htm)

---


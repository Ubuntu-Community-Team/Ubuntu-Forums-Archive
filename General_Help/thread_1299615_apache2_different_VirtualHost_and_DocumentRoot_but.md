---
title: "apache2 different VirtualHost and DocumentRoot but accessing the same directory/file"
date: 2009-10-24
forum: General Help
---

### Post by lxq on 2009-10-24
Hello guys!

I found something odd on the apache VirtualHost configuration today. Inside the /etc/apache2/sites-available I have created two different virtualhost configuration file. After that I enabled the site by using a2ensite command and then reload apache by /etc/init.d/apache2 reload. Inside the /etc/hosts I have also divided them into different IP. But it turned out when I try to access them through browser they seems to be pointing to the same directory.

Is there something wrong on the configuration? Please help me.

Here are the virtualhost configuration I created.

/etc/apache2/sites-available/phpweb
```
<VirtualHost *:80>
	ServerName phpweb
	ServerAdmin [email]admin@phpweb.com[/email]

	DocumentRoot /var/www/phpweb/htdocs/
	DirectoryIndex index.php index.html
	<Directory /var/www/phpweb/htdocs>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		Options All
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/phpweb/cgi-bin/
	<Directory "/var/www/phpweb/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	php_value include_path .:/var/www/phpweb/include:/usr/local/lib/pear
	php_value magic_quotes_gpc off
	php_value register_globals off

</VirtualHost>
```

/etc/apache2/sites-available/testweb
```
<VirtualHost *:80>
	ServerName testweb
	ServerAdmin admin@testweb

	DocumentRoot /var/www/testweb/htdocs/
	DirectoryIndex index.php index.html
	<Directory /var/www/testweb/htdocs>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		Options All
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/testweb/cgi-bin/
	<Directory "/var/www/testweb/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	php_value include_path .:/var/www/testweb/include:/usr/local/lib/pear
	php_value magic_quotes_gpc off
	php_value register_globals off

</VirtualHost>
```

/etc/hosts
172.19.23.1	phpweb
172.19.24.1	testweb

Thanks in advance.

---


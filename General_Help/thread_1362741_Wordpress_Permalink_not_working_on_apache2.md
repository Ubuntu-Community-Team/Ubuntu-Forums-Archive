---
title: "Wordpress Permalink not working on apache2"
date: 2009-12-23
forum: General Help
---

### Post by helyos on 2009-12-23
I can solve this issue. I try to enable permalink for my blog but it doens't work! Now let me tell you the details:

- I have ubuntu 8.04 

- -in my blog's directory i have the .htaccess (777 permissions) file with the following content:

```
# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress

<Files 403.shtml>
order allow,deny
allow from all
</Files>

deny from 88.198.207.4
deny from 88.198.36.73
deny from 91.214.44.231
deny from 91.214.44.230
```

-Apache directives in /etc/apache2/sites-available/

```
ServerAdmin contact@test.com
ServerName test.com
        ServerAlias http://www.test.com

DocumentRoot /home/admin/path/siteroot
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>

<Directory /home/admin/path/siteroot>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

<Directory /home/admin/path/siteroot>
		Options FollowSymLinks
		AllowOverride All
</Directory>
```

- mod_rewrite it's on

Please help me because i really don't know what's happening!

---

### Post by helyos on 2009-12-27
no ideeas??

---


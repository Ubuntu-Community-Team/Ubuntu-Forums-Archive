---
title: "phpmyadmin over SSL"
date: 2011-06-13
forum: General Help
---

### Post by goodvikings on 2011-06-13
I'm trying to set up phpmyadmin to use ssl on a server I have running, but I want other parts of the website to not use ssl. Ideally they would set up as subdomains, like so:

[https://phpmyadmin.goodvikings.com](https://phpmyadmin.goodvikings.com)
[http://blog.goodvikings.com](http://blog.goodvikings.com)

versions:

Apache2 version 2.2.8-1ubuntu0.19
php5 version 5.2.4-2ubuntu5.17
phpmyadmin version 4:2.11.3-1ubuntu1.3

I can get one or the other to work: both ssl or both not. I can also get it to kinda work, where phpmyadmin.goodvikings.com will work, but no files in the directory will (not even index.php)

file contents:
/etc/phpmyadmin/apache.conf - edited from default config to be virtual host
```

# phpMyAdmin default Apache configuration

# Alias /phpmyadmin /usr/share/phpmyadmin

<VirtualHost phpmyadmin.goodvikings.com> only the phpmyadmin login page works
# <VirtualHost *> all subdomains try to use the ssl
DocumentRoot /usr/share/phpmyadmin
ServerName phpmyadmin.goodvikings.com

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/phpmyadmin.pem
SSLVerifyClient none
</VirtualHost>

```
/etc/apache2/sites-available/blog.goodvikings.com.conf
```

<VirtualHost *>
DocumentRoot /var/www/wp
ServerName blog.goodvikings.com
<Directory "/var/www/wp">
allow from all
Options +Indexes
</Directory>
SSLEngine off
</VirtualHost>

```

Any ideas?

Cheers

Ramo

PS. Check out my computer security blog at blog.goodvikings.com :D

---

### Post by goodvikings on 2011-06-14
Hate to do it, but here's a nice bump. Could really use a hand on this.

---

### Post by goodvikings on 2011-06-14
They see me bumpin

---

### Post by besterino on 2011-08-25
I had exactly the same problem and could not find a solution on the web that met my requirements. This is what I did:
 
System: ubuntu server 10.04LTS
Assumptions (i.e. this was my system and it worked): installed and running Apache2, any SSL-enabled virtualhost (site), php5, MySQL and phpmyadmin (each installed from ubuntu repositories with apt-get install).
 
Step 1: Delete symlink /etc/apache2/conf.d/phpmyadmin.conf (pointing to ../../phpmyadmin/apache.conf).
**sudo rm /etc/apache2/conf.d/phpmyadmin.conf** 
 
Step 2: Edit your SSL-virtualhost in /etc/apache2/sites-available/[mySSLsite] and insert "Include /etc/phpmyadmin/apache.conf" in the line above "< /virtualhost >".
 
Since I am totally new to all of this myself, I do not expect this to be the cleanest or most secure way. But it has the charm of being very very easy to accomplish... (without having to dig into the details of the mysql/php/phpmyadmin configs)...
 
Comments, yes please!
 
Edit: If I were you I would try to set up a SSL-secured virtualhost/site before mixing SSL with phpmyadmin. You should be able to accomplish that by using the resources available. If you have your SSL-site running properly, the above should work without a problem.

---


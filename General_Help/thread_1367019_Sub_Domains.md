---
title: "Sub Domains"
date: 2009-12-29
forum: General Help
---

### Post by rabidityfactor on 2009-12-29
Hi. I'm trying to create a subdomain sub.domain.com. I have configured an Apache server. DNS configuration has been done with zoneedit.com.

So basically I have a domain - www.domain.com - and it works perfectly. I wanted to add a subdomain - sub.domain.com.
The config file **/etc/apache2/sites-available/domain** is as follows

```
NameVirtualHost *

<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName domain.com
	DocumentRoot /home/ceaadmin/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/user/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

<VirtualHost *>
  ServerAdmin webmaster@localhost
  DocumentRoot /home/user/sub_html
  ServerName sub.domain.com
  ErrorLog /home/ceaadmin/logs/sub-error.log
  CustomLog /home/ceaadmin/logs/sub-access.log common
  <Directory />
          Options FollowSymLinks
          AllowOverride None
  </Directory>
  <Directory /home/user/sub_html/>
          Options Indexes FollowSymLinks MultiViews
          AllowOverride All
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

 # Possible values include: debug, info, notice, warn, error, crit,
 # alert, emerg.
 LogLevel warn

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

But now the problem is that when I enter **http://sub.domain.com/**, I get the _index page of www.domain.com_. That is, basically it does not read **/home/user/sub_html/index.html**. But if I specify some other pages like - **http://sub.domain.com/my_page** - it works.

What am I doing wrong?
Thanks in advance

---


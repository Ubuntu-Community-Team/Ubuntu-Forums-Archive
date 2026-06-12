---
title: "cannot access a website from windows host to ubuntu guest virtual box"
date: 2012-05-07
forum: General Help
---

### Post by angelogasa on 2012-05-07
good morning

i installed ubuntu as guest os using virtualbox to use as web server then installed the necessary software like apache php etc.

now my problem is if i type the ip address of the guest os i get the it works! default page of apache but if i type the ip address plus the directory example 192.168.0.9/directory it couldnt find it and the host os is capturing it instead of the guest os the address will now be localhost/directory

can someone help me how can i setup ubuntu to allow me to view a webpage on hosted inside ubuntu guest os

note:the network protocol is bridge

---

### Post by jerome1232 on 2012-05-07
It could be your webserver permisions, if I recall correctly Apache doesn't let you descend down the folder hierarchy in the default config. This is an example of what my apaches config is, I'm not that advanced with this stuff so it's entirely possible my configuration sucks, but it works. :D

This particular site is stored in my the user "voiceserv"s ~/public_html folder. Anything below that folder is accessible.
```
jeremy@voiceserv:~$cat /etc/apache2/sites-available/voiceserv 
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/voiceserv/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/voiceserv/public_html/>
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

```

---

### Post by angelogasa on 2012-05-07
did you give permission to apache as the owner of the directory you gave as example?

so you are saying that i should not put any directory in /var/www?

---


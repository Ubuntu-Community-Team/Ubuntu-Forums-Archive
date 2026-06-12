---
title: "is there an easy way to make mysite.com and www.mysite.com point to the same folder"
date: 2009-12-05
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-05
Hello, I am running the latest Ubuntu and have set up Apache2. After playing a little I've added a new domain mysite.com. Everything works fine but now I want to have [www.mysite.com](www.mysite.com) that points to the same place. I went to /etc/apache2/sites-enabled and it now looks like this:
```

<VirtualHost *:80>
	ServerAdmin webmaster@mysite.com
	ServerName mysite.com
	DocumentRoot /home/eugene/server/mysite/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/eugene/server/mysite/>
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

<VirtualHost *:80>
	ServerAdmin webmaster@mysite.com
	ServerName www.mysite.com
	DocumentRoot /home/eugene/server/mysite/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/eugene/server/mysite/>
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

```

As you can see I've just copy-pasted the section for mysite.com and added www. for the server name. It works just fine but doesn't look very elegant. Please tell me if that's how it is supposed to be or have I missed an easier way to do this?

---

### Post by w1n78 on 2009-12-06
the second virtual host isn't necessary

you need to edit the /etc/hosts file
it should say something like

127.0.0.1          mysite.com
127.0.0.1          [www.mysite.com](www.mysite.com)

---

### Post by Eugene_Bondarenko on 2009-12-06
I've tried removing that second section but now when I type [www.mysite](www.mysite), I get into localhost directory.

---

### Post by w1n78 on 2009-12-06
> **Eugene_Bondarenko said:**
> I've tried removing that second section but now when I type [www.mysite]("http://www.mysite"), I get into localhost directory.

sorry, i think you do need that second virtualhost. just copy your first one and change ServerName to the www version.

---

### Post by Eugene_Bondarenko on 2009-12-06
Sure, that's fine, thanks for the help! I am totally fine with this solution but since I am a bit new to this I was not sure that I did everything correctly and that's how it is supposed to be.

---


---
title: "MOD_Rewrite problem"
date: 2010-02-20
forum: General Help
---

### Post by ctult on 2010-02-20
Help!  I enabled mod_rewrite by running sudo a2enmod rewrite but it says it is already enabled.  But then I try Mod_rewrite out and it does not work.

EDIT: I used .htaccess. is there any configuration?

---

### Post by Halibutt on 2010-03-26
Instead of starting a new topic I'll reuse this one, maybe someone will help us here. I'm trying to enable mod_rewrite on my 9.10 LAMP. Sadly, to no avail. 

I tried the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=7304"). In short, the procedure runs fine, but then when I restart Apache with

```
sudo /etc/init.d/apache2 restart
```

The result is:
```

halibutt@halibutt-laptop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Syntax error on line 207 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Can't locate API module structure `mod_rewrite' in file /usr/lib/apache2/modules/mod_rewrite.so: /usr/lib/apache2/modules/mod_rewrite.so: undefined symbol: mod_rewrite
```

Meaning: fail. 

Yet, the link "rewrite.load" is there in ../etc/apache2/mods-enabled, when trying to "sudo a2enmod rewrite" it tells me it's already been done, I allowed for AllowOverride in ../etc/apache2/sites-available/000-default:

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride all
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
```

Yet, the error is still there and now my local Wordpress installation doesn't work at all. Any suggestions? Please?
Cheers

---


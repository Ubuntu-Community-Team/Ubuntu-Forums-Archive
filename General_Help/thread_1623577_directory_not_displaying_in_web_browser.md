---
title: "directory not displaying in web browser"
date: 2010-11-16
forum: General Help
---

### Post by fndtn357 on 2010-11-16
I have a LAMP environment on Ubuntu 9.04 desktop. I created a directory in /home/user that I use for all my development work called /projects.

I am able to access this directory via localhost/projects as the URI in my web browser; I see a listing of all the separate directories and I am able to click on each directory and see its contents.
_Parent Directory_
_Site-Structure/_       30-Aug-2010  11:39
_builds/_               03-Sep-2010  00:02
_d6/_                   12-Nov-2010  13:25
_d7/_                   31-Oct-2010  17:44
_domain1.com/_          17-Aug-2010  22:48
_domain2.com/_          17-Aug-2010  22:48
_drupal6_modules/_      05-Nov-2010  16:28
_drupal7_modules/_      05-Nov-2010  15:20
_mapsonastick/_         19-Aug-2010  00:01
_profiles/_             30-Oct-2010  10:46
_temp/_                 31-Oct-2010  06:59
_theming/_              31-Oct-2010  12:04

**Except one, d6/!**

When I click on the directory localhost/projects/d6 I get this error:

[SIZE="3"]Forbidden[/SIZE]
_You don't have permission to access /projects/d6 on this server._
*Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.6 with Suhosin-Patch Server at localhost Port 80*

**This is my most used and accessed directory.  I used to be able to access this directory and now I can't.**

My /etc/apache2/sites-enabled directory has a file called projects with this information in it:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/james/projects/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/james/projects/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		Allow from all
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

    Alias /phpmyadmin/ "/var/www/phpmyadmin/"
    Alias /phpmyadmin "/var/www/phpmyadmin/"
    <Directory "/var/www/phpmyadmin/" >
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
	Deny from none
    </Directory>

</VirtualHost>
```

I have default, default-ssl and projects in my /etc/apache2/sites-available directory. I haven't changed these files since I first created them.  I haven't changed the permissions on any of the directories within /home/user/projects since I first set this up.

**What can I do to access this directory from the address bar of a browser again?**

---

### Post by lmarmisa on 2010-11-16
Could you post the output of this command?

```

ls -l /home/james/projects/

```

---

### Post by fndtn357 on 2010-11-16
james@zorba:~$ ls -l /home/james/projects/
total 52
drwxrwxrwx  3 james james 4096 2010-09-03 00:02 builds
drwxrwxrwx 13 james james 4096 2010-11-13 15:24 d6
drwxrwxrwx  6 james james 4096 2010-11-13 18:29 d7
drwxrwxrwx  7 james james 4096 2010-08-17 22:48 domain1.com
drwxrwxrwx  7 james james 4096 2010-08-17 22:48 domain2.com
drwxrwxrwx  4 james james 4096 2010-11-05 16:28 drupal6_modules
drwxrwxrwx  2 james james 4096 2010-11-05 15:20 drupal7_modules
drwxrwxrwx  8 james james 4096 2010-08-19 00:01 mapsonastick
drwxrwxrwx  5 james james 4096 2010-10-30 10:46 profiles
drwxrwxrwx 14 james james 4096 2010-11-05 15:20 projects
drwxrwxrwx 11 james james 4096 2010-08-30 11:39 Site-Structure
drwxrwxrwx  6 james james 4096 2010-11-15 16:37 temp
drwxrwxrwx  3 james james 4096 2010-10-31 12:04 theming

---

### Post by lmarmisa on 2010-11-17
The output looks good.

Try this other command:

```

ls -l /home/james/projects/d6/

```

---

### Post by fndtn357 on 2010-11-17
james@zorba:~$ ls -l /home/james/projects/d6/
total 44
drwxrwxrwx 11 james james 4096 2010-11-15 03:39 clevelandbankruptcy.bartosandrini.com
drwxrwxrwx  9 james james 4096 2010-08-11 16:41 d6api
drwxrwxrwx 11 james james 4096 2010-11-13 19:45 divorceattorney.bartosandrini.com
drwxrwxrwx  9 james james 4096 2010-08-24 11:10 drupal_atrium
drwxrwxrwx  9 james james 4096 2010-08-16 18:36 drupal_commons
-rwxrwxrwx  1 james james  380 2010-09-25 22:36 featureserver.make
drwxrwxrwx  9 james james 4096 2010-09-25 22:50 fserver
drwxrwxrwx  9 james james 4096 2010-08-11 16:41 guardianadlitemproject.org
drwxrwxrwx 11 james james 4096 2010-10-02 00:24 module-dev
drwxrwxrwx  9 james james 4096 2010-08-11 16:41 rdf
drwxrwxrwx 10 james james 4096 2010-11-13 18:25 uwsfc.org


this output looks good too. This is why it doesn't make any sense to me.

---


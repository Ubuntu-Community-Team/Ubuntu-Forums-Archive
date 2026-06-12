---
title: "HTML include allowing with apache"
date: 2012-10-01
forum: General Help
---

### Post by micahpage on 2012-10-01
sorry if this is the wrong area, i couldn't find an area that deemed decent for this subject.


I have an apache server running from ubuntu.

I have came across the problem of copy/pasting the same html code from one page to the other to get my "header", "navigation bar" etc. on each web page. I currently have the code pasted on each web page to get the header and navigation bar on each, but I see the problem as I change it.

I came across the code to include an html page to another html page
```
<!--#include virtual="insertthisfile.html" -->
```

but I can't get it to work. I am also confused on this html code because I understand it as comments for html? Why would a comment be executed?

I was told to change the config for apache and this is what I have came acrossed and changed it to:


> /etc/apache2/sites-available/default
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options +ExecCGI Indexes FollowSymLinks MultiViews +Includes
		#AllowOverride None
		Order allow,deny
		allow from all
		AddHandler cgi-script .py 
                AddHandler default-handler .html .htm  
		AddType text/html .shtml
		AddHandler server-parsed .html
		AddHandler server-parsed .shtml
		DirectoryIndex index.shtml index.html
	</Directory>

	#ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	#<Directory "/usr/lib/cgi-bin">
		#AllowOverride None
		#Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		#Order allow,deny
		#Allow from all
	#</Directory>
	
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		#AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch Includes
		Order allow,deny
		Allow from all
		AddHandler cgi-script .py 
                AddHandler default-handler .html .htm  
		AddType text/html .shtml
		AddHandler server-parsed .html
		AddHandler server-parsed .shtml
		DirectoryIndex index.shtml index.html
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

Is the order in which it is arranged here matter?
Am I missing something from this to config file to allow me to include html files?
I am not exactly sure what this file is, I just added/changed lines as forum people have told me to. A description of this file would be helpful in me understanding this.

I have also tried changing the file to include to .shtml, but didn't get it to work either

---

### Post by Lars Noodén on 2012-10-01
Have you turned on the module for includes?

```

sudo a2enmod include
sudo apache2ctl restart

```

Also, you might consider using the option IncludesNOEXEC instead of Includes.

Check /var/log/apache2/error.log for relevant errors.

---

### Post by micahpage on 2012-10-01
> ```
sudo a2enmod include
```
i did not know about this, thank you

I did try this and restarted server, but I didn't see a change with anything included


This is the recent error.log, but nothing regarding that specific file
```
Mon Oct 01 06:18:19 2012] [notice] caught SIGTERM, shutting down
[Mon Oct 01 06:18:20 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Mon Oct 01 06:18:25 2012] [error] [client 69.205.235.224] File does not exist: /var/www/mystyle.css, referer: http://www.metulburr.com/index.html
[Mon Oct 01 06:18:25 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:18:27 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:18:28 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:18:29 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:18:30 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:32 2012] [error] [client 69.205.235.224] File does not exist: /var/www/mystyle.css, referer: http://www.metulburr.com/index.html
[Mon Oct 01 06:19:32 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:38 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:39 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:44 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:44 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Mon Oct 01 06:19:44 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Mon Oct 01 06:19:48 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:54 2012] [error] [client 69.205.235.224] File does not exist: /var/www/mystyle.css, referer: http://www.metulburr.com/
[Mon Oct 01 06:19:54 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:55 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:19:57 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:20:01 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:20:05 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:20:09 2012] [error] [client 69.205.235.224] File does not exist: /var/www/mystyle.css, referer: http://www.metulburr.com/index.html
[Mon Oct 01 06:20:09 2012] [error] [client 69.205.235.224] File does not exist: /var/www/favicon.ico
[Mon Oct 01 06:21:44 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Mon Oct 01 06:21:44 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Mon Oct 01 06:23:44 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
[Mon Oct 01 06:23:45 2012] [error] [client 127.0.0.1] File does not exist: /var/www/announce
```



> you might consider using the option IncludesNOEXEC instead of Includes.
I am not sure what exactly you mean by this

---

### Post by Lars Noodén on 2012-10-01
With the error log, does anything come up when you load the .shtml page or when you reload Apache's configuration file?  You can follow the output of the error log live with [tail](http://manpages.ubuntu.com/manpages/precise/en/man1/tail.1.html)

```

tail -f /var/log/apache2/error.log 

```

---

### Post by micahpage on 2012-10-01
i ran that error log, and didnt see anything



EDIT:
I am not sure what i did or if it was your method of enabling the include, but when i ran it and checked, it did not work, and now after rechecking the site, it does have the include in it.


Thank you

Do i have to enable this every time of reboot or just a one time thing?

---

### Post by Lars Noodén on 2012-10-01
It was probably a2enmod that did it.  It's a one-time thing.  It will stay on until you turn it off again.  You can turn it off with a2dismod.

IncludesNOEXEC is a variation of the option Includes, but does not allow scripts to be run.  It is just adding a bit of security if you will not be running scripts via SSI.
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

---


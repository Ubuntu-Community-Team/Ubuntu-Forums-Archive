---
title: "html downloaded from public_html"
date: 2010-08-07
forum: General Help
---

### Post by Peter Simple on 2010-08-07
In ubuntu 10.04, I created ~/public_html/index.html and enabled userdir.

When I browse to [http://localhost/~user/index.html](http://localhost/~user/index.html) the page is downloaded, not opened (tested on Chrome and Firefox).

However, browse to file:///home/user/public_html/index.html and the page is opened correctly. Other web pages also open correctly.

Why would a browser download an html page in public_html?

---

### Post by darolu on 2010-08-07
Are your permissions OK?

---

### Post by Peter Simple on 2010-08-07
AFAIK. The page is downloaded correctly, so the browser can read it properly.

Both /home/user and /home/user/public_html have 755 permissions. The web page itself has 644.

---

### Post by WorMzy on 2010-08-07
Sounds like a misconfigured web server. I assume you're using Apache?

Check /etc/apache2/sites-enabled/<sitename> and make sure that you've correctly set up home directories. It should have something like this:

```
UserDir public_html
<Directory "/home/*/public_html">
    AllowOverride FileInfo AuthConfig Limit Indexes
    Options MultiViews Indexes SymLinksIfOwnerMatch ExecCGI
    <Limit GET POST OPTIONS>
        Order allow,deny
        Allow from all
    </Limit>
    <LimitExcept GET POST OPTIONS>
        Order deny,allow
        Deny from all
    </LimitExcept>
</Directory>
```

---

### Post by Peter Simple on 2010-08-07
Thanks. I suspect the apache2 config, but don't see anything wrong. I checked your suggestion, restarted apache2 and get the same problem.

Below are contents of httpd.conf and sites-enabled/000-default:

--- httpd.conf ---
AddType application/x-httpd-php .html
ServerName localhost

--- sites-enabled/000-default ---
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

    UserDir public_html
    <Directory "/home/*/public_html">
    AllowOverride FileInfo AuthConfig Limit Indexes
    Options MultiViews Indexes SymLinksIfOwnerMatch ExecCGI
    <Limit GET POST OPTIONS>
        Order allow,deny
        Allow from all
    </Limit>
    <LimitExcept GET POST OPTIONS>
        Order deny,allow
        Deny from all
    </LimitExcept>
    </Directory>

</VirtualHost>

---

### Post by WorMzy on 2010-08-07
Forget what I said earlier, it works a littler differently on Ubuntu to other Linux OS', instead of adding that stuff about /home/*/public_html, you just need to create symlinks for userdir.conf and userdir.load (from /etc/apache2/mods-available) in /etc/apache2/mods-enabled.

So first check /etc/apache2/mods-enabled for those two link, and if they don't exist, then create them by opening a terminal and running
```
cd /etc/apache2/mods-enabled && sudo ln -s /etc/apache2/mods-available/userdir.conf && sudo ln -s /etc/apache2/mods-available/userdir.load
```

Also, remove the stuff I asked you to add to your default site config (if you added it).

---

### Post by gmargo on 2010-08-07
The proper way to adjust the "mods-enabled" links is to use the **a2enmod(1)** and **a2dismod(1)** commands. (See also the **a2ensite(1)** and **a2dissite(1)** commands for the "sites-enabled" links.)

---

### Post by Peter Simple on 2010-08-07
I had run a2enmod already, and do have the symlinks.

I added the extra on UserDir to the default config as earlier suggested, and have now removed it. 

So I am back at square one - the behavior is still the same as originally stated.

---


---
title: "403 error after changing apache2 document root"
date: 2012-01-01
forum: General Help
---

### Post by Autarchist on 2012-01-01
Hi folks, thanks for your time.

I decided to change the apache document root from **/var/www** to my home folder, **/home/blair/www**

I followed this video tutorial: youtube.com/watch?v=qw95e7eWZEw

Basically I created the new **www** directory in **/home/blair**, and then modified the **/etc/apache2/sites-available/default**:

> <VirtualHost *:80>
ServerAdmin webmaster@localhost

**DocumentRoot /home/blair/www**
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

</VirtualHost>As you can see I simply modified the the fourth line down from **/var/www** to **/home/blair/www**

Then, I restarted apache by running **sudo /etc/init.d/apache2 restart**

Now, when I point my browser to [http://localhost](http://localhost), I get **403 Forbidden** error.

I might be way off, I'm speculating it might be that apache2 does not have permission to access the new **www** folder. If this is the case, how can I grant such access?

Thanks again!

---

### Post by squaregoldfish on 2012-01-01
My document root is owned by www-data. So:

chmod www-data:www-data <dir>

As long as all the files in that directory are world-readable, things should be OK.

Steve.

---

### Post by rsvancara on 2012-01-01
You can do:

sudo su - www-data

and then 

ls -las /home/blair/www 

to evaluate the permissions as www-data.

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by Autarchist on 2012-01-01
I ran:

** sudo chgrp www-data /home/blair/www**


> **rsvancara said:**
> You can do:

sudo su - www-data

and then 

ls -las /home/blair/www 

to evaluate the permissions as www-data.

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

And then:

[B]sudo su - www-data
ls -las /home/blair/www[/B]

and was told **ls: cannot access /home/blair/www: Permission denied**

When I right-click on the new **www** directory in my home folder and choose properties -> permissions, it says it is owned by **www-data**. Access is still denied (403) when I try to load **[http://localhost](http://localhost)**.

One of the reasons I wanted to move the documentroot from the **/var/www** was so that I didn't need root privileges to make changes at any time. If that is not possible, I'm sure I will adapt to it, but I'm wondering if there is a way to share privileges between **www-data** and my user account.

---


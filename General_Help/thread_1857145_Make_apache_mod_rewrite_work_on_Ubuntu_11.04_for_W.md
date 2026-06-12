---
title: "Make apache_mod_rewrite work on Ubuntu 11.04 for WordPress website"
date: 2011-10-09
forum: General Help
---

### Post by AndrewStarlike on 2011-10-09
I develop a Wordpress website on localhost and i need custom permalinks for some AJAX functionality built with "pretty" urls in mind.

I followed steps like:
[PHP]
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart
[/PHP]
So apache mod rewrite is already installed. But is not working ( yes i am a little bit angry by the way )!

I also changed some config like:
[PHP]
Options Indexes FollowSymLinks MultiViews
AllowOverride **all**
Order allow,deny
allow from all
[/PHP]

Wordpress default htaccess rules are:
[PHP]

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /devhelper.orgdev/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /devhelper.orgdev/index.php [L]
</IfModule>

# END WordPress
[/PHP]

And restart the server. Still not working! That kind of "page not found" not working. I use .htaccess for over a year and didn't had this kind of problems untill i made the decision to use Ubuntu instead of Windows. 
You cannot really be pist off when an install should work out of the box and it isn't! You know what really makes me angry: on the host server everything works fine, on my PC it doesn't. And both run Linux... I have literally spended hours in fixing this issue instead of developing things!!!
And still doesen't work...

---

### Post by mikejonesey on 2011-10-09
always trial and error bugs like these, its the fastest way to solve a silly problem... try first with, adding an include or direct rewrites in the virtualhost to confirm it works there...

---

### Post by Dangertux on 2011-10-09
> **AndrewStarlike said:**
> I develop a Wordpress website on localhost and i need custom permalinks for some AJAX functionality built with "pretty" urls in mind.

I followed steps like:
[PHP]
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart
[/PHP]So apache mod rewrite is already installed. But is not working ( yes i am a little bit angry by the way )!

I also changed some config like:
[PHP]
Options Indexes FollowSymLinks MultiViews
AllowOverride **all**
Order allow,deny
allow from all
[/PHP]Wordpress default htaccess rules are:
[PHP]

# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /devhelper.orgdev/
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /devhelper.orgdev/index.php [L]
</IfModule>

# END WordPress
[/PHP]And restart the server. Still not working! That kind of "page not found" not working. I use .htaccess for over a year and didn't had this kind of problems untill i made the decision to use Ubuntu instead of Windows. 
You cannot really be pist off when an install should work out of the box and it isn't! You know what really makes me angry: on the host server everything works fine, on my PC it doesn't. And both run Linux... I have literally spended hours in fixing this issue instead of developing things!!!
And still doesen't work...

No need to get that frustrated, I sugges creating the .htaccess file manually this is the one that I use and it works fine with LAMP + Ubuntu Server 10.04 + Wordpress

```


# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

```Also make sure it is owned by root with at least permissions 644. Hope that helps :-)

Also your virtual host configuration should have the following present

```

<Directory />
Options Follow SymLinks
AllowOverride All
</Directory>

```

Watch your capitalization your All was all, this makes a difference.

---

### Post by AndrewStarlike on 2011-10-09
Thanks a lot guys, i was angry because i was so tired.

It's been 2 days since i passed on Ubuntu and i managed to make everything work so far excluding the above.

There was such a silly problem, i feel so bad now.

For those in the same situation:

After i installed apache2 i had to change a rule with the help of the terminal:

[PHP]sudo vi /etc/apache2/sites-available/default[/PHP]

And this command returns:

[PHP]
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
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
[/PHP]

As you can see there are two "AllowOverride All" rules for the same folder. Because i was tired i didn't saw the second one... I changed it and everything works perfect now :guitar:

---

### Post by andperry on 2012-08-13
I'm having exactly the same problem (using Ubuntu Server 12.04). Have tried the instructions given in this thread - to do the manual edit to .htaccess and to alter the two 'AllowOverride' directives to 'All'. Problem still occurs even after rebooting the machine. Any more ideas?

Thanks,

Andrew.

---


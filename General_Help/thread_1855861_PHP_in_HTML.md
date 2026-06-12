---
title: "PHP in HTML"
date: 2011-10-07
forum: General Help
---

### Post by lapsus on 2011-10-07
Hello,

I am developing a simple website and working on Ubuntu 11.04.
The html pages contain also php (include). I installed apache2, php5 etc and seems to be working. When I copy my html files to /var/www and type localhost/ in the browser (I use chormium) everything seems OK.
However, when I just open any html file in my home folder php elements are not visible.
(I also use a local .htaccess file for php in html.)

Is there any way how to see pages with php from my home directory without copying them to /var/www ?

Thank you!

---

### Post by ianhaycox on 2011-10-07
PHP is processed by Apache not the browser, so your pages have to be served by Apache.

To save copying to /var/www try enabling the userdir module,

```
$ mkdir ~/public_html
$ sudo a2enmod userdir
$ sudo /etc/init.d/apache2 restart
```

The dump all your files in ~/public_html and browse to [http://localhost/~youruser](http://localhost/~youruser)

Ian.

---

### Post by lapsus on 2011-10-07
Thank you! This works well :-)

And is it possible to see the php page from any other folder?
In fact I don't want to publish the page from my computer, I just want to see the result before copying it to the server.

---

### Post by ianhaycox on 2011-10-07
As usual there are loads of different ways, but what I do is,

1. Install the Apache module to allow Apache to run as my user

```
$ sudo apt-get install apache2-mpm-itk
```

2. Create a virtual host, by creating a file in /etc/apache2/sites-available/mysite with the contents,

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	ServerName mysite

	DocumentRoot /home/ian/Projects/mysite
	<Directory /home/ian/Projects/mysite>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	<IfModule mpm_itk_module>
	AssignUserId ian ian
	</IfModule>

	ErrorLog /var/log/apache2/mysite-error.log
	CustomLog /var/log/apache2/mysite-access.log combined

</VirtualHost>

```

Adjust your paths and userid as appropriate.

3. Edit /etc/hosts to append mysite to localhost

```

127.0.0.1	localhost mysite

```

4. Create the 'projects' directory above, e.g. /home/ian/Projects/mysite and dump a 1 line index.html file there with hello world

5. Enable site and restart Apache

```

$ sudo a2ensite mysite
$ sudo /etc/init.d/apache2 restart
```

6. Browse to [http://mysite](http://mysite)  and see 'hello world'

Rinse, repeat for more sites.

I've got about 20 virtual hosts with Wordpress, Drupal etc. installed in each Projects directory, for theme, plugin development

Ian.

---

### Post by lapsus on 2011-10-07
Thaks, Ian!
This works perfectly.

---


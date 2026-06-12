---
title: "Forbidden message on Apache (file rights)"
date: 2012-06-08
forum: General Help
---

### Post by ebekkema on 2012-06-08
Hello all,

First I want to let you know I'm new to Linux, so please take it easy ;)

When I access my website, a 403 Forbidden message is displayed.
And this is why I think why:

I changed the default /var/www/ directory to /home/bert/public_html/
(used this tutorial [link]("https://help.ubuntu.com/community/ApacheMySQLPHP"))

> Virtual Hosts

Apache2 has the concept of sites, which are separate configuration files that Apache2 will read. These are available in /etc/apache2/sites-available. By default, there is one site available called default this is what you will see when you browse to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1). You can have many different site configurations available, and activate only those that you need.

As an example, we want the default site to be /home/user/public_html/. To do this, we must create a new site and then enable it in Apache2.

To create a new site:

Copy the default website as a starting point. sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 

Edit the new configuration file in a text editor "sudo nano" on the command line or "gksudo gedit", for example: gksudo gedit /etc/apache2/sites-available/mysite

Change the DocumentRoot to point to the new location. For example, /home/user/public_html/

Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>

You can also set separate logs for each site. To do this, change the ErrorLog and CustomLog directives. This is optional, but handy if you have many sites

Save the file
Now, we must deactivate the old site, and activate our new one. Ubuntu provides two small utilities that take care of this: a2ensite (apache2enable site) and a2dissite (apache2disable site).


sudo a2dissite default && sudo a2ensite mysite
Finally, we restart Apache2:


sudo /etc/init.d/apache2 restart
If you have not created /home/user/public_html/, you will receive an warning message

To test the new site, create a file in /home/user/public_html/:


echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.html
Finally, browse to [http://localhost/](http://localhost/)

This worked perfect! No problems so far.

Then I installed an FTP server (vsftpd)
(used this tutorial [link]("https://help.ubuntu.com/10.04/serverguide/ftp-server.html"))

Also FTP worked fine. On my windows machine I connect (with Dreamweaver) to the Linux FTP Server and can login to my account en put files into the public_html directory.

But the files I put via FTP has different rights and cannot read by Apache. A 403 Forbidden message is displayed.
When I give more rights to the website files then it works fine:
sudo chmod -R 755 /home/bert/public_html/

As an example:
[IMG]http://img843.imageshack.us/img843/7254/86201272856.png[/IMG]

index.html was put by FTP (from windows)
index2.html was created manual (on linux)

How can I get the FTP files to get the same rights as index2.html? 
Is there another option?

Hopefully you can help me understand and fix this issue.

Thanks.

---

### Post by ebekkema on 2012-11-07
I had to set the following in /etc/vsftpd.conf

local_umask=022

---

### Post by Lars Noodén on 2012-11-07
Can you post the exact error from the Apache error log?  That would help with the 403 error.

However, the correct way to set up [Per-user Web Directories](http://httpd.apache.org/docs/2.2/howto/public_html.html) is to use the module *mod_userdir*  You can enable the module with [a2enmod](http://manpages.ubuntu.com/manpages/precise/en/man8/a2enmod.8.html).

```

sudo a2enmod userdir

```

Then adjust the access permissions in your virtual host's configuratin file and reload the web server.  If you haven't changed anything the default vhost file is in /etc/apache2/sites-available/default

```

UserDir public_html
<Directory /home/*/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride AuthConfig Indexes
        Order allow,deny
        allow from all
</Directory>

```

---


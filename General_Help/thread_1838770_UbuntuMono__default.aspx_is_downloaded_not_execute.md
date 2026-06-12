---
title: "Ubuntu/Mono : default.aspx is downloaded not executed"
date: 2011-09-04
forum: General Help
---

### Post by NewBeInTarn on 2011-09-04
Hello everybody, I try to activate Mono on Ubuntu 11.04 server (without gnome).
When I try the URL [http://192.168.2.159/testsitewebpourmono/](http://192.168.2.159/testsitewebpourmono/), Ubuntu list all files, and with default.aspx, Ubuntu download it instead of execute.

I have publish my dummy web site in /var/www/, from a Windows desktop with samba.

Apache is configure with 

```
<VirtualHost *:80>
    ServerAdmin myadress
    ServerName Dummy.com
    MonoAutoApplication disabled
    AddHandler mono .aspx ascx .asax .ashx .config .cs .asmx .axd
    MonoApplications "/:/var/www/testsitewebpourmono"
         MonoServerPath default /usr/bin/mod-mono-server2

    DocumentRoot /var/www/testsitewebpourmono/
    <Directory />
             Options FollowSymLinks
             AllowOverride None
    </Directory>
         <Directory /var/www/testsitewebpourmono>
                 Options Indexes FollowSymLinks MultiViews
                 AllowOverride All
                 Order allow,deny
                 allow from all
                 SetHandler mono
                 DirectoryIndex default.aspx Default.aspx index.aspx index.html
         </Directory>


         ErrorLog /var/log/apache2/error.log

         # Possible values include: debug, info, notice, warn, error, crit,
         # alert, emerg.
         LogLevel warn

         CustomLog /var/log/apache2/access.log combined
 </VirtualHost>
```

I have installed mono with
```
sudo apt-get install libapache2-mod-mono mono-apache-server2
sudo a2enmod mod_mono
sudo service apache2 restart
```

And activate the web site with 

> sudo a2ensite testsitewebpourmono
sudo /etc/init.d/apache2 restart

What is wrong with my test ?

(sorry for my poor english...)

---


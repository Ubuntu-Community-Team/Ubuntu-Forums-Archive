---
title: "Ruby with apache ActionController::RoutingError (No route matches &quot;/&quot;):"
date: 2010-10-05
forum: General Help
---

### Post by kristensson.jonas on 2010-10-05
Hi!

I an trying to setup ruby on rails with apache server on ubuntu server
10.04. I have followed toe guid on the ubuntu page.

My main app is located in:

/home/jonas/ruby/apps/rtest1/public

and I created a symlink to /var/www/app using the following command:

sudo ln -s /home/jonas/ruby/apps/rtest1/public /var/www/app

I have also reconfigured the owner of the /home/jonas/ruby/apps/rtest1/
public and /home/jonas/ruby/apps/rtest1/tmp to www:data.

this is my apache.conf file:

<VirtualHost *:80>
       ServerAdmin webmaster@localhost
       DocumentRoot /var/www
       RailsEnv production
       RailsBaseURI /app
       <Directory /app>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride All
               Order allow,deny
               allow from all
       </Directory>

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

       # Possible values include: debug, info, notice, warn, error,
crit,
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


But when I try to access my program through localhost/app I get error
404 and in the production.log i find:

Started GET "/app" for 192.168.1.3 at Tue Oct 05 18:18:24 +0200 2010

ActionController::RoutingError (No route matches "/"):

All my php software still runs fine under localhost though.

This is probably easy to fix but I have been trying for days and still
can't get it to work, whats wrong?

---


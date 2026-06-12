---
title: "Configuring apache virtual hosts for public web"
date: 2010-12-02
forum: General Help
---

### Post by jjei on 2010-12-02
Hi,

I am trying to configure apache virtual hosts for a subdomain to work in public web, not just my localhost.
I have read the instructions here 
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2) and here 
[http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html](http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html) but I still can get it work.

I have a domain1.fi that works. Typing [http://domain1.fi](http://domain1.fi) in browser shows index.html that is located in /var/www/index.html

Now I need to configure test.domain1.fi to point /var/www/test/

My /etc/apache2/sites-available/test.domain1.fi.conf has:

<VirtualHost test.domain1.fi>
ServerAdmin webmaster@localhost
ServerAlias [www.test.domain1.fi]("http://www.test.domain1.fi") 
DocumentRoot /var/www/test 
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

And then I have /etc/apache2/sites-enabled/test.domain1.fi pointing to the above mentioned file.

I am not sure what I should put in /etc/hosts. I have tried to add for example the following entries and restarting apache without success:
[ip-address of domain1.fi]  test.domain1.fi and
domain1.fi  [ip-address of domain1.fi] test.domain1.fi

What should I put in the hosts file?

Do I need to do some stuff to a records? They were mentioned at some instructions but I did not understand do I need them in this case.

Why are the instructions different for the apache configuration (in every tutorial they are slightly different)?

For example:

<VirtualHost dev.example.com>
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com]("http://www.dev.example.com") or dev.example.com
ServerAlias [www.dev.example.com]("http://www.dev.example.com")
DocumentRoot /home/myuser/public_html/example.com
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>

And:
<VirtualHost *>
  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin [EMAIL="webmaster@site2.com"]webmaster@site2.com[/EMAIL]
  ServerName  site2.com
  ServerAlias [www.site2.com]("http://www.site2.com")


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /home/me/web/site2.com/


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/me/web/site2.com/logs/error.log
  CustomLog /home/me/web/site2.com/logs/access.log combined
</VirtualHost>

Thanks in advance!

---


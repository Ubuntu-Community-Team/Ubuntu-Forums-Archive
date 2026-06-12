---
title: "Virtual Server - Can u spot the not?"
date: 2010-03-26
forum: General Help
---

### Post by gomenor on 2010-03-26
Hi guys,

I'm trying to get "Virtual hosting" with 1 domain to work on my Ubuntu Server. My experiance isn't too overwelming, but I belive that I'm closing in on the solution.

I would like MyDomain.se work with the directory: var/www/wordpress.


And this is the guide I've been using: [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
This is what is in my etc/apache2/sites-enabled/wordpress.conf:

<VirtualHost domainname.se>
ServerName domainname.se
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.exa$
ServerAlias [www.domainname.se](www.domainname.se)
DocumentRoot /var/www/wordpress
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/wordpress-access.log combined
</VirtualHost>This is what's in my etc/hosts:

127.0.0.1 localhost.localdomain localhost domainname.se [www.domainname.se](www.domainname.se)
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So when I write "http://domainname.se" In web browser I get this html text written on my page:

"Apache is functioning normallySo my domain is working - but it seems to be accessing the wrong root directory."

So my domain seems to be working - but it looks like it's accessing the wrong root directory.

Can anyone help me look into this,
or help me troubleshoot the problem?

Thank you!

---


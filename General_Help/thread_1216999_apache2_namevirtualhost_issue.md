---
title: "apache2 namevirtualhost issue"
date: 2009-07-18
forum: General Help
---

### Post by quantumelody on 2009-07-18
Hello,

I have been trying (unsuccessfully) to get Wordpress working on my Ubuntu 9.04 laptop for the past two months. My problem seems to be with apache2.

When I check to see if apache2 is working, Firefox and Opera tell me that [http://127.0.0.1](http://127.0.0.1) and [http://localhost](http://localhost) are both unavailable. I tried to restart apache using the command sudo /etc/init.d/apache2 restart, and it gave me the following errors:

[Sat Jul 18 23:17:15 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
(98 ) Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

I have tried reading other areas for help on this issue, and no one seems to have any idea how to help those with this problem. I have also tried to purge and reinstall apache2, thinking that it would in fact remove any damaged configuration files, but none of my config files disappeared because they're still the same after a restart and fresh install. I have done this via the terminal AND Synaptic Package Manager. In addition, I ran system updates to make sure that my issues weren't coming from any problems with outdated versions.

Could someone please give me information on how to resolve this problem?

Also, I have been to the "[How to Install Wordpress]("http://www.jonathanmoeller.com/screed/?p=932")" page, but the writer seems to assume that apache2 will magically work by bribing it with sudo sugar ... so its instructions will be of no use until I get apache2 working.

Thanks in advance.

---

### Post by utnubuuser on 2009-07-19
lullabot has a great video on installing apache and drupal, and I've installed wordpress using the same directions.

here's the link> [http://www.lullabot.com/node/289]("http://www.lullabot.com/node/289")

---


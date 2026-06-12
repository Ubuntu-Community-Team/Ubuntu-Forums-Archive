---
title: "server 10.10 - access from LAN to virtual hosts"
date: 2010-10-22
forum: General Help
---

### Post by canucksailor on 2010-10-22
Apache 2.2 on server 10.10 all running well, except that virtualhosts is not functional as expected. All other LAN boxes are Win XP Pro SP2 and can see the ubuntu server2 (hard coded IPs for LAN, no DHCP.) 192.168.0.20 is NameVirtualHost on the ubuntu server2.

Set up 4 websites (sdb/www/site1, sdb/www/site2, etc, not using public_html) and the corresponding entries in hosts and sites-enabled - all accessible from Firefox on server2. HOWEVER, from the XP boxes on the LAN they were not directly visible using [http://site1](http://site1) (they were visible for a request [http://server2/site1](http://server2/site1) but this was bypassing virtualhosts and going straight to the directory proved it by adding site5 with no corresponding VirtualHost in sites-enabled). After modifying the Win hosts file to add lines 192.168.0.20 site1, 192.168.0.20 site2, etc all functioned as expected but is probably still finding the directory rather than the VirtualHost.

This to me appears to be Win forcing the address at http request level, rather than ububtu/apache resolving via virtualhosts. Am I correct? and if so how do I get apache to resolve correctly?

That is, is there anyway to reference a named virtual host via apache without adding entries into each client host file?

Is there any other syntax that I can type into a client browser to reference a named virtual host without going through the hosts file?

Many thanks - Paul
[first post to the forum]

---

### Post by perspectoff on 2010-10-22
This isn't really an Ubuntu question. You might have better luck in the Apache forums:

[http://www.apache.com/forums/index.php](http://www.apache.com/forums/index.php)

---


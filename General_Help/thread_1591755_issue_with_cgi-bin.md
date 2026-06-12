---
title: "issue with cgi-bin"
date: 2010-10-09
forum: General Help
---

### Post by fieldway on 2010-10-09
Hi

Trying to get ryanseds ([http://www.equitasit.co.uk/ryanseds](http://www.equitasit.co.uk/ryanseds)) going on my Ubuntu Server (9.04)

I created a cgi-bin directory under /var/www and chmod 777 cgi-bin

I edit /etc/apache2/sites-avaliable/default and change the scriptalias path of the cgi-bin to /var/www/cgi-bin 

When I try to open folder on the net (10.1.1.3/cgi-bin) it come back with an error saying “*You don't have permission to access /cgi-bin/ on this server.*” And below it, it say “*Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.6 with Suhosin-Patch Server at 10.1.1.3 Port 80*”
 
I got Drupal6 (10.1.1.3/drupal6) and Moddle (10.1.1.3/moodle) running on this server without any problem.

How do I fix this wee issue?


thanks

---


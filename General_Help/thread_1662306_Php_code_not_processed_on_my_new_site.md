---
title: "Php code not processed on my new site"
date: 2011-01-07
forum: General Help
---

### Post by Chien_Fu on 2011-01-07
I just got my new vps up and running.I'm very new to ubuntu but I now have one site hosted on the server using drupal.  Apache,php, mysql are all set up and working fine.  I tried to setup a second site and created another virtual host for it.  All permissions are set the same, the two virtual hosts have all the same settings but the new site does not process my php.  When I browse to the new site I get a blank page.  By viewing the source I can see that the php code is coming in but it is not being processed.

Don't know enough to know what else to check. Please help.
Thanks.

---

### Post by Chien_Fu on 2011-01-08
[SIZE=2]Okay, 
After more searching around I discovered that the term it seems I should be using is Apache is not "parsing" my php.
[/SIZE][SIZE=2]I have an info.php file that works fine and claims:  "[/SIZE][SIZE=2]PHP Version 5.2.6-3ubuntu4.6"

So I have

 /var/www/info.php   -  Works fine
 /var/www/site1/index.php    -  Works fine
 /var/www/site2/index.php    -  PHP NOT PARSED!~

What could be going on here?
[/SIZE]

---

### Post by Chien_Fu on 2011-01-12
I had deleted my .htaccess file from one of my drupal installs in case anyone cares...

---


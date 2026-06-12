---
title: "Installing Joomla on Ubuntu 10.04"
date: 2010-08-18
forum: General Help
---

### Post by criptonite on 2010-08-18
Hi, I cannot get Joomla to install.

I have a working LAMP stack (Apache2, PHP5 and Mysql).  I installed them without problem following instructions on this forum, ran the suggested tests and they seem to be absolutely fine.

I have also followed the instructions for install Joomla on this thread [https://help.ubuntu.com/community/Joomla%201.5]("https://help.ubuntu.com/community/Joomla%201.5")

I can't see what I've missed.  The only area where things don't seem right is when I restart Apache2

The command is: sudo /etc/init.d/apache2 restart

And the response is:

* Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I can point my browser to 127.0.1.1 and also to localhost/ and will have the "It Works" screen appear.

When I point to localhost/joomla  I a told the link is broken (Google Chrome browser) and the same happens for 127.0.1.1/joomla.

I originally started out with Xampp but couldn't see the localhost page at all so uninstalled xampp and went down the LAMP route.

Incidentally, I have also installed Drupal via Synaptic and it worked first time. which suggests that the LAMP stack is ok.

Help please

---

### Post by zaazz on 2010-09-02
I just was trying to test out Joomla 1.6Beta on my new install of ubuntu 10.04 and now I'm having this same problem. I can go into /var/www and delete the index.html file yet when I go to local host it still gives me the "It Works" screen. So there may be more then one issue here, Joomla contents are not showing up and apache2 isn't pointing localhost or people browsing to my IP at the correct location.

---


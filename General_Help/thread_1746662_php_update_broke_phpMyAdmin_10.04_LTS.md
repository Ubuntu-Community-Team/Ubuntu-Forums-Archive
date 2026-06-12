---
title: "php update broke phpMyAdmin 10.04 LTS"
date: 2011-05-02
forum: General Help
---

### Post by spoolboyy on 2011-05-02
Hello,

I am having an issue with phpMyAdmin on my Xubuntu machine.  I installed a few updates today and now my phpMyAdmin web interface site is not loading on the server.  This is a local server running in my office.  It appears that the page tries to load, but no output is delivered to the screen.

Taking a closer look at my updates, it looks like the following changes were made (along with some upgrades to Firefox):



Commit Log for Sun May  1 12:12:04 2011

Upgraded the following packages:
libapache2-mod-php5 (5.3.2-1ubuntu4.7) to 5.3.2-1ubuntu4.8
php5 (5.3.2-1ubuntu4.7) to 5.3.2-1ubuntu4.8
php5-common (5.3.2-1ubuntu4.7) to 5.3.2-1ubuntu4.8
php5-gd (5.3.2-1ubuntu4.7) to 5.3.2-1ubuntu4.8
php5-mysql (5.3.2-1ubuntu4.7) to 5.3.2-1ubuntu4.8


When I use the 'Force Version....' command, I am given only two options the '4.8' version that I have now (the broken one) and a flat '4' version with no .7.  Also, the force version didn't seem to do anything.  I tried to Force a version and then mark a package for reinstall.  When I did this Synaptic informed me that it was simply going to reinstall the 4.8 version.  

What I would like to do is to revert to the 5.3.2-1ubuntu4.7 version of all of these files and then lock the version using Synaptic, to prevent this issue from recurring.  Can anyone help me out with some instructions to revert?  I am not an expert, but I am not afraid of heading to the command line either.

Any help would be greatly appreciated.  Thank you VERY MUCH in advance!

-Spool

System Information:
   32-Bit Xubuntu 10.04 LTS install
   Athlon 3800+
   2GB Ram

---

### Post by spoolboyy on 2011-05-02
Nevermind.  This will do it.  Thanks anyway.

[http://www.nickveenhof.be/blog/reverting-or-downgrade-php-53-52-ubuntu-lucid-lynx-1004](http://www.nickveenhof.be/blog/reverting-or-downgrade-php-53-52-ubuntu-lucid-lynx-1004)

---


---
title: "problem in xampp-&gt;lamp setup"
date: 2012-01-19
forum: General Help
---

### Post by ahasan_al_rabbi on 2012-01-19
I'm new user of ubuntu 11.10 . I've already download xampp for linux and extract it in /opt.
when i command this line > sudo /opt/lampp/lampp startIt's show this lines > Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
Warning: World-writable config file '/opt/lampp/etc/my.cnf' is ignored
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP for Linux started.MySQL, phpmyadmin not starting... 
what will i do? :(

---

### Post by satanselbow on 2012-01-19
This really is not a flippant answer and designed to help you mucho grief now and later down the line ;)

1. Uninstall XAMPP
2. Following the excellent guide on the community pages here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

XAMPP installs itself in non default locations and masks some pretty essential configuration options under a poorly designed, buggy gui... I'm not a fan if you hadn't guessed ;)

If you have any further problems then come back and ask here - there will be many more people familiar with a standard LAMP stack installation than the mess that be XAMPP.

---


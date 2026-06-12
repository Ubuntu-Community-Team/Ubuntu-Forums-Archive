---
title: "Are XAMPP and KDE incompatible?"
date: 2010-06-12
forum: General Help
---

### Post by olwe on 2010-06-12
Out of desperation in trying to get Drupal to do multi-sites, I've tried to totally uninstall Apache-MySQL-PHP and install XAMPP. I used synaptic to uninstall, and the apt-got versions of Apache and PHP seem to go away fine. However, MySQL is not going peacefully. Synaptic lists "mysql-client-core-5.1" and mysql-server-core-5.1" and when I try to click to remove, it wants to take out a whole list of supposedly unrelated stuff, one of them being kubuntu-desktop. I did it once -- and kde was sure enough gone. I came back in in Gnome, did apt-get kubuntu-desktop, got kde back (all old setting just fine). The reinstall seemed to only be putting a "akondai-server" back.

Good. XAMPP is in and good. But when it starts it says "Another MySQL daemon is already running." System Monitor/Processes shows nothing MySQL running, though. But then a root "ps -aux" does show a "/usr/sbin/mysqld" running.  I reboot and it's still there. What is this mysqld and how do I get rid of it? Is KDE needing/using it? I kill -9 it, and XAMPP starts fine with no MySQL conflict, but where and why is this mysqld still running after a supposed remove?

Basically, I just want to work on multiple Drupal sites on my home computer and not have world-class production versions of AMP running, just a simple XAMPP.

---


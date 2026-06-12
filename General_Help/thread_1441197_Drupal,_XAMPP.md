---
title: "Drupal, XAMPP"
date: 2010-03-28
forum: General Help
---

### Post by tamobe on 2010-03-28
Running Karmic Koala and wanted to play with/test Drupal. I muddled installations of XAMPP and Drupal and I've been attempting to reset everything (apache, PHP, MySQL) so I could try and start over from the beginning again. But everytime there I try re-installing and starting over there seems to be problems with Apache or PHP or MySQL.

Anyone have any suggestions as to how to reset all the Apache, PHP, MySQL settings? Unfortunately I know very little about it all - do I need to just remove them all using Synaptic?

Thank you!

---

### Post by isbiyanto on 2010-05-06
> **tamobe said:**
> Running Karmic Koala and wanted to play with/test Drupal. I muddled installations of XAMPP and Drupal and I've been attempting to reset everything (apache, PHP, MySQL) so I could try and start over from the beginning again. But everytime there I try re-installing and starting over there seems to be problems with Apache or PHP or MySQL.

Anyone have any suggestions as to how to reset all the Apache, PHP, MySQL settings? Unfortunately I know very little about it all - do I need to just remove them all using Synaptic?

Thank you!

I am newbie too. but drupal working well on me.
I just need XAMPP. download here : [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by WorMzy on 2010-05-06
I've seen so many people installing XAMPP over the past few days, and I have no idea why! Just install LAMP (sudo tasksel install lamp-server), and add libapache2-mod-perl2 (sudo apt-get install libapache2-mod-perl2). Then any perl files in /var/www/cgi-bin will execute when you call them.

I can't help you remove your xampp settings, but I think the installation files normally ask to be moved to /opt.

---


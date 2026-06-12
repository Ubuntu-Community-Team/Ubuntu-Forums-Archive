---
title: "Suggestion for XAMPP on Ubuntu"
date: 2011-08-29
forum: General Help
---

### Post by Scottty on 2011-08-29
Hello

I went to the Apache friends website here [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

I am going to try their procedure on how to install XAMPP on Ubuntu 11.04

Or is there a better way to install MySQL,PHP and Apache on my system.

I just wanted to ask before I mess my system up.

Thank-you
Scott

---

### Post by PsyclonJohn on 2011-08-29
LAMP is the best way!

Installation directions: [http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/](http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/)

---

### Post by mcduck on 2011-08-30
I agree with PsyclonJohn, since we have a native LAMP stack, supported by Ubuntu's developers and installable through package management, it really makes sense to use that instead of any third-party solutions.

---

### Post by Scottty on 2011-08-30
> **PsyclonJohn said:**
> LAMP is the best way!

Installation directions: [http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/](http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/)

Hello

I followed all the instructions and everything went exactly as Planned
untill I came to the last part.
> 
I also noticed, people were having problem with PHPMYADMIN not showing up in /var/www. This is how you fix it.

While inside Root’s File System using the code above, go to /usr/share/phpmyadmin and copy and paste that folder to var/www

I cannot go to /usr/share/phpmyadmin and copy and paste that folder to var/www

I was able to copy paste into my HOME folder but I can't copy paste into the var/www folder.

How can I enable this action. Is it because the system doesn't see me as being Root

---

### Post by PsyclonJohn on 2011-11-09
Sorry for the extra long response...

It will only work if you are still in the root file system (using gksudo nautilus only), if not you won't be able to create any new files within /var/www

Hope this helps :)

---


---
title: "phpmyadmin install issue"
date: 2010-05-05
forum: General Help
---

### Post by Masked Crusader on 2010-05-05
Hey all.

I just purchased the ve server from Media Temple.  It comes with just a default install of Unbuntu.  I have had to figure out how to install everything to make the server LAMP ready.  

I have gotten Apache2, PHP5, and mySQL installed.  The problem that I am having now is trying to access phpmyadmin.  I am getting the beautiful 404 error :)

I installed phpmyadmin, but the only copy I can find is in my root/etc/ folder.  I am wanting the phpmyadmin to be installed in my root/var/www so that I can access phpyadmin at the end of my domain or IP.  So, "whatever.ip/phpmyadmin".

Am I missing a step here?  

I did sudo apt-get install phpmyadmin and it asked me to enter in my mySQL crendentials and then asked me for administrator password for phpmyadmin.  I entered all that in and I just cannot figure out how to get it so that I can access phpmyadmin via my IP or domain name.

Any help would be appreciated.

Thanks!

---

### Post by Masked Crusader on 2010-05-05
I just tried to follow these steps: [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

My problem I think is the location of my phpMyAdmin.  I believe it should be in the var/www directory instead of the /etc/ directory.

---

### Post by Masked Crusader on 2010-05-06
Figured it out.

Used this line right here: 

*sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin*

That creates the link that was necessary.

Hope this helps someone else!

---


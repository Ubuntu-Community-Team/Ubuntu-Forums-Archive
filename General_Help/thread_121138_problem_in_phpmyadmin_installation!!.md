---
title: "problem in phpmyadmin installation!!"
date: 2006-01-24
forum: General Help
---

### Post by dtygel on 2006-01-24
Hi all,

   I've just installed, without much hassle, mysql-php-apache. Now when I install phpmyadmin (via apt-get or synaptic), it just doesn't work: it appears that apache has some restrictions in accessing php in phpmyadmin directory, because when I type: "localhost/phpmyadmin", the mozilla browser simply asks me to save the folder! 

    I tested php, and it works allright (I've created a index.php file with just "phpinfo()" in it, and it worked!). I also tested several other directories under localhost (/var/www) and they worked as well: html and php. Is there some configuration, some "htaccess" or something similar which I should configurate? :confused:

***:D Solved:*** It was a problem with the mozzilla's cache! Sorry for bothering the forum with such a simple question...

       Thanks a lot,

               daniel tygel (from brasil)

---


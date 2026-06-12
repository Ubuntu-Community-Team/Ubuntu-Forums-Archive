---
title: "lamp configuration permissions"
date: 2010-03-08
forum: General Help
---

### Post by anatak on 2010-03-08
I installed lamp (php) and I can access the default site and my phpmyadmin pages.

Now I have a few questions
1 
What is the best way to create a folder where you can put your html/ php files so that apache2 can serve them ?
I created a folder on my Desktop: /home/bob/Desktop/bike
then I copied and modified the sites-available default file to reflect the path
 or would it be better to create a folder in /var/www/bike
create a symbolic link to the desktop and work in that folder ?

2 
I ran the 
a2dissite default and the
a2ensite bike
restart apache

I made an index.html file but when I browse to [http://bike/](http://bike/)
I get the message that I am not allowed to access / on the server.

how do I change this ?

thank you
anatak

---


---
title: "php my admin"
date: 2009-11-14
forum: General Help
---

### Post by malikge on 2009-11-14
Hello... 
I am using ubuntu 8.10 and I have installed LAMP (Apache and php) on my system. I have used the guide from the following site:

              [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Apache and php have installed perfectly, and running. But I don't know how to use MySql. In windows I use to enter:
              [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
and mysql starts.
But after the installation in linux when I open up the browser and enters the link of phpmyadmin it give the message:
                    
                    NOT FOUND
                    The requested URL /phpMyAdmin was not found on this server.
                     Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.3 with Suhosin-Patch Server at localhost Port 80

Can anyone tell me how to fix it and how to run it???
Thanks...

---

### Post by markjensen on 2009-11-14
Hey, I am just starting along this road too.  I installed xampp on a Windows box at work for testing, and it was effortless and "just worked".

However, doing a **sudo apt-get install phpmyadmin** on my Xubuntu box at home *seemed* to pull in all that was needed, I get a login screen and cannot login.

During install, I was prompted for a password for access, which I supplied.  But I get:
#1045 - Access denied for user 'root'@'localhost'
(using password: YES)

I got a little further than you, I think, because I pointed my browser to the address as follows:
[http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)

See if that works for you. And, if so, how are you able to log in and get to administer your databases?

---

### Post by Tiganjero on 2009-11-14
Are you sure that you started Lampp? ```
/opt/lampp/lampp start
``` By the way phpMyAdmin is supposed to come with Lampp.

---


---
title: "Xampp phpmyadmin"
date: 2012-08-09
forum: General Help
---

### Post by Omer Aslam on 2012-08-09
I installed Xampp. when i open [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) it gives this error.
**Access forbidden!**

             You don't have permission to access the requested directory.     There is either no index document or the directory is read-protected.      
   If you think this is a server error, please contact the [EMAIL="you@example.com"]webmaster[/EMAIL].  
   **Error 403**

     [localhost]("http://localhost/")
  Apache/2.4.2 (Unix) OpenSSL/1.0.1c PHP/5.4.4

kindly tell me what to do..............?

---

### Post by mastablasta on 2012-08-09
change permissions in the web server's folder to www-data user or if you are only testing you can add yourself to the group with permission in that folder

---

### Post by Omer Aslam on 2012-08-09
thanks for you reply.....

but can you tell me how to change permissions..i am new linux user and don't know much about linux and xampp..actualy first i used wamp in windows and it works perfectly...

---

### Post by mastablasta on 2012-08-10
that's because in windows everyone has permissions to use those folders (including malware...).
 
if you have desktop installed you just go to directoy: /var/www
right click on www directory, propperties and then change permissions.
 
if you have CLI server only then see here:
[http://askubuntu.com/questions/19898/whats-the-simplest-way-to-edit-and-add-files-to-var-www](http://askubuntu.com/questions/19898/whats-the-simplest-way-to-edit-and-add-files-to-var-www)
 
you should add the user to the group so that you can change files in the direcoty more easilly.

---


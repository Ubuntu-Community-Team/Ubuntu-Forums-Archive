---
title: "LAMP: mod_rewrite, imagick refuses to work in one folder"
date: 2011-02-19
forum: General Help
---

### Post by NaGeL on 2011-02-19
hello alll.

Okay. I have ubuntu 10.10. I installed apache2 Php mysql and phpmyadmin through the package handler. it worked after that I instaled Imagemagick , and imagick for PHP. than I installed mod_rewrite for appache2. I created a folder in /var/www/ called shimmie. I copied there my codes and  after setting up htaccess it worked fine.  url rewrite worked. thumbnails with imagick appeared along with normal images. Yesterday  I got another webpage  project. but it required apache mod_ expires and mod_headers and installed it. And installed Xdebug for PHP.  after this I put  the  webpage to another /var/www/ folder called fashion. Now in fashion everything works as its needs to: url rewrite , expires.. everything. But now my original folder shimmi, doesnt works: no url rewrite, no imagick thumbnails nor the original image shows up.

the folder belongs to my user and set is that every thing can read it and write it.

help me please

EDIT: I even copied the shimmie folder toa new and still didnt work, so i re created it... and still doesn&#8217;t work.... why is thats the only thing that cant use .htacces and imagick?
 [http://paste.ubuntu.com/569115/](http://paste.ubuntu.com/569115/) this is my  sites-enabled/000-default file
 [http://paste.ubuntu.com/569117/](http://paste.ubuntu.com/569117/) the modsenabled on apache2
  [http://paste.ubuntu.com/569118/the](http://paste.ubuntu.com/569118/the) last lines of error.log
 [http://paste.ubuntu.com/569120/](http://paste.ubuntu.com/569120/) and my phpinfo()

---

### Post by NaGeL on 2011-02-19
please help me, my job hangs on this!

---


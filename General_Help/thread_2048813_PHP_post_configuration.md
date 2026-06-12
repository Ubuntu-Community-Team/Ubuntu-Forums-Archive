---
title: "PHP post configuration"
date: 2012-08-27
forum: General Help
---

### Post by ludo1960 on 2012-08-27
Hello,

On my debian box I have LAMP configured and working well. I now want to add a script that has these pre-requisites:

PHP 5.0.2+ with the following libraries installed.     
[LIST]
[*]--with-apxs2=/usr/local/apache2/bin/apxs
[*]--with-mysql
[*]--with-zlib
[*]--with-curl
[*]--enable-mbstring
[*]--with-gd
[*]--with-jpeg-dir=/usr/lib
[/LIST]
How do I go about making sure these dependences are met? I see mysql and zlib in my phpinfo.php. What I should really be saying is I'm a newbie and not got a clue what to do!

Thanks..

---

### Post by spjackson on 2012-08-27
mysql, zlib - you can see these in phpinfo, as you said.
mbstring - you should be able to see this in phpinfo too.

curl & gd - you need to install the packages php5-curl and php5-gd, then phpinfo should show these, after restarting apache.

   --with-jpeg-dir=/usr/lib

I'm not 100% sure about this, but if you install php5-gd, then I think phpinfo will show gd with jpeg enabled.

apxs2=/usr/local/apache2/bin/apxs
I can't help with this one.

---

### Post by ludo1960 on 2012-08-27
Thanks for the info, that helped a lot. Cheers. 

As for apxs2=/usr/local/apache2/bin/apxs I'm struggling with that one, hopefully someone out there knows what to do... here's hoping!

---

### Post by ludo1960 on 2012-08-27
yeah gd says:

JPEG Support enabled 

But how do I find out if it is the mythical apxs2? I don't have /usr/local/apache2.. directory so I think not. any ideas?

---

### Post by spjackson on 2012-08-29
As I understand it, apxs2 is used to compile apache modules. If you have the right modules installed, which it appears you do, then you don't need to compile any.

If you do need it, then you need to install the development package that matches your apache installation. e.g. if you have apache2-mpm-prefork installed, then you would need apache2-prefork-dev etc. These packages won't put apxs2 in /usr/local/... I don't understand why the pre-requisites for your script insist on it being there.

Have you tried installing and running the script you want to run?

---


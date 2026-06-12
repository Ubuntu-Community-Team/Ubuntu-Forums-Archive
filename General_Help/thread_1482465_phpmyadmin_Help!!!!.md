---
title: "phpmyadmin Help!!!!"
date: 2010-05-13
forum: General Help
---

### Post by DaleHUtch on 2010-05-13
Greetings everyone....

Well I have tried everything I can think of and anything on a google search.

What I'm trying to do it secure the phpmyadmin folder.

I put a .htaccess file in /usr/share/phpmyadmin

I can still just can't get it to pop up a required username and password...

Does anyone have suggestions??

Thank you!

---

### Post by DaleHUtch on 2010-05-13
Well I don't know what I did...

I guess the server needed to be restarted for some reason. 

After the reboot phpmyadmin is not secure.

Ubuntu is a really cool OS. I'm learning!

Thanks

---

### Post by zunk on 2011-03-20
I've got a similar problem. After hours and hours of googling where to put the htaccess file and get stuff to work I've put  this:
```
Order Deny,Allow
Deny from All
```
in this file
"/etc/phpmyadmin/apache.conf".

And it all works, but whenever i add say
"allow from x.x.x.x",
the allow changes nothing.

What am I doing wrong and am I even editing the correct file? And why cant I just put a .htaccess file in "/usr/share/phpmyadmin"? The info should easy to find, but it isn't afaik.

ps. I've set "AllowOverride All" in the "/etc/apache2/sites-available/default"-file.

---

### Post by haafmaad on 2011-03-20
in your phpmyadmin directory there should be a config.inc.php file.

open the file and edit the 'auth' type lines like this

'auth_type' lines:
             $cfg['Servers'][$i]['auth_type']     = 'config';
        $cfg['Servers'][$i]['user']          = 'root';
        $cfg['Servers'][$i]['password']      = 'secret';

set a password restart your xampp or phpmyadmin. Now it'll require a password. Cheers

---

### Post by zunk on 2011-03-22
I wanted it to not be accessible per .htaccess rule from outside of my internal ip-range. I "solved" by using a different-than-standard alias. Not a solution but no sane person will find it anyway ; )

---

### Post by Matt_Fussell on 2012-01-16
I know it's a good deal after the fact, but this may help as well:
[http://ubuntuforums.org/showpost.php?p=11615996&postcount=9](http://ubuntuforums.org/showpost.php?p=11615996&postcount=9)

---


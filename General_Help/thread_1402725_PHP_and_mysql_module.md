---
title: "PHP and mysql module"
date: 2010-02-09
forum: General Help
---

### Post by pspeakman on 2010-02-09
Sorry to cross post, but someone suggested if I get no response I should.

This is really killing me now and any other ideas would be appriciated:

I've upgraded to newest ubuntu and found that mysql didn't work with php when I did so - I'm on a power PC, which has some issues with Flash (i.e. it doesn't work) but everything else has been fine.
I have found many others with this problem and followed all the suggestions but it still doesn't work.

root@ubuntu:/usr/lib/php5/ext# dpkg --list | grep php5-mysql
ii php5-mysql 5.2.10.dfsg.1-2ubuntu6 MySQL module for php5

Tells me that it's installed.
But i still get this:
Fatal error: Call to undefined function mysql_connect() in ....

---

### Post by theDaveTheRave on 2010-02-23
to be able to use php  etc you need to have the following in the apache config file /etc/apache2/httpd.conf

```

UserDir disabled root
#to enable the use of PHP, load the required module
LoadModule php5_module modules/libphp5.so

# this would be the "normal" apache config lineAddType application/x-httpd-php php
#but we are using the suggested format from php for the config as follows
<FilesMatch \.php$>
          SetHandler application/x-httpd-php
</FilesMatch>

```

there may be something you need to add in the php installation as well, but I think it worked straight off the bat for me. it was just apache I needed to play with...

David

---


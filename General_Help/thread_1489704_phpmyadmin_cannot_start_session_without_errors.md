---
title: "phpmyadmin cannot start session without errors"
date: 2010-05-21
forum: General Help
---

### Post by pmiln099 on 2010-05-21
I haven't found a suitable solution yet to my problem. While using phpmyadmin under priveleges I added a password for a user. Now I get the error:
> Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

My searching so far seems to point to something to do with permissions for the session.save_path file (/var/lib/php5).
I can see the owner for the folder is root with create/delete priveleges. Inside the folder, the session file has owner www-data with read/write access. (I can see in phpinfo() that www-data is the user/group for apache)

Am I on the right track: needing to change permission for these files?
How do I do that?
Is there some other problem I am overlooking?

Thx

---

### Post by wojox on 2010-05-21
See if this helps at all [phpMyAdmin]("https://help.ubuntu.com/10.04/serverguide/C/phpmyadmin.html")

---


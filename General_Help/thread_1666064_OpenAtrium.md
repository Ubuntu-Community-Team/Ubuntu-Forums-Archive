---
title: "OpenAtrium"
date: 2011-01-13
forum: General Help
---

### Post by EmyrB on 2011-01-13
Hi All,

OK, this is going to sound like a noob question so I will offer appologies right off the bat. I am currently administrating a server we have inherited. It's running Zentyal which is based on Ubuntu 10.04. I have been given the task of backing up all user data, including data users have added through OpenAtrium. Now for the life of me I cannot find where this data is. OpenAtrium uses Apache, PHP, MySQL and Drupal so any hints on data location would be great so I can get Bacula to backup this important data.

Again, apologies for the noob-like question.

Cheers

EmyrB

---

### Post by James78 on 2011-01-13
Backup all the files on the server. Then, using something like phpmyadmin, backup the database. If phpmyadmin isn't installed, you could probably just upload and install it temporarily (forget about creating the phpmyadmin database, you won't need that if you're just going to delete phpmyadmin afterward)
[http://www.phpeveryday.com/articles/PhpMyAdmin-Backup-Database-using-PhpMyAdmin-P119.html](http://www.phpeveryday.com/articles/PhpMyAdmin-Backup-Database-using-PhpMyAdmin-P119.html)
[http://www.phpeveryday.com/articles/PhpMyAdmin-Backup-Database-using-PhpMyAdmin-P120.html](http://www.phpeveryday.com/articles/PhpMyAdmin-Backup-Database-using-PhpMyAdmin-P120.html)

---


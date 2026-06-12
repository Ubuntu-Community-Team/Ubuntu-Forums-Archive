---
title: "Drupal install causing &quot;Read-only file system&quot; error?"
date: 2006-02-17
forum: General Help
---

### Post by cloneofsnake on 2006-02-17
Not sure if I should post it here or at Drupal.org, but I'll try here first.  I've recently set up Ubuntu w/ Apache, PHP & MySQL.  I was trying to install the Drupal CMS on it.  I came to step 4 on this [installation instruction]("http://drupal.org/node/43807") page, where I have to define the **db_url** and **base_url** in the **settings.php** file:

[INDENT][I][COLOR="Blue"][SIZE="2"]Open the configuration file and edit the
$db_url line to match the database defined in the previous steps:
$db_url = "mysql://username:password@localhost/drupal";
Set $base_url to match the address to your web site:
$base_url = "http://www.example.com";[/SIZE][/COLOR][/I][/INDENT]

(This file is located on /var/www/drupal-4.6.5/sites/default/settings.php)  I made a copy by doing cp ./settings.php ./settings.php.backup, made the changes, saved it.  Didn't work.  Threw me this error:

[INDENT][I][COLOR="Blue"][SIZE="2"]Warning: mysql_connect() [function.mysql-connect]: Host 'localhost.localdomain' is not allowed to connect to this MySQL server in
/var/www/drupal-4.6.5/includes/database.mysql.inc on line 31 Host 'localhost.localdomain' is not allowed to connect to this MySQL server[/SIZE][/COLOR][/I][/INDENT]

The next day, I looked into the database.mysql.inc file, line 31... obviously the db_url variable in settings.php isn't being passed correctly as it still has "localhost.localdomain".  I went back to setting.php.  Tried to make changes to it... but somehow, it threw me a warning saying I'm "making changes to a read-only file system".  I thought it was only a user permission thing.  I exited vi, changed to root user, same thing!  I then tried to remove the file and start over... same thing:

[INDENT]*[COLOR="Blue"][SIZE="2"]rm: cannot remove `settings.php': Read-only file system[/SIZE][/COLOR]*[/INDENT]

and even more weird, it started spamming me with this message:

[INDENT]*[COLOR="Blue"][SIZE="2"]postdrop: warning: mail_queue_enter: create file maildrop/250425.8476: Read-only file system[/SIZE][/COLOR]*[/INDENT]

Pops up every 5 seconds... I can't even exit out of terminal now!  Any idea?

Thanks!!

---

### Post by dcstar on 2006-02-17
[QUOTE=cloneofsnake]
.......
[INDENT]*[COLOR="Blue"][SIZE="2"]postdrop: warning: mail_queue_enter: create file maildrop/250425.8476: Read-only file system[/SIZE][/COLOR]*[/INDENT]

Pops up every 5 seconds... I can't even exit out of terminal now!  Any idea?

Thanks!![/QUOTE]
Boot up in Recovery mode and run fsck, hopefully that will fix the filesystem.

---

### Post by cloneofsnake on 2006-02-19
OK, I boot into safe mode and it stopped at /var... asked me to provide root password, then it showed a lot of "problems" and I need to press y to fix or clear things.  After that, I tried to run shutdown but it doesn't work, so I reset.

Now I can't boot into ubuntu regularly.  I tried booting into safe mode again, it now says: /ect/init.d/rcS: line 27: /etc/default/rcS: file not found.  It asks me to provide root password for maintainence again.  I did and then tried to run fsck again, but it now says bash: fsck: command not found.

Not sure what to do next... please help! :cry:

---

### Post by cloneofsnake on 2006-02-20
bump.

---


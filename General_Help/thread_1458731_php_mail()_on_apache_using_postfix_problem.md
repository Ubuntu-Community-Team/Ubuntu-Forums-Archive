---
title: "php mail() on apache using postfix problem"
date: 2010-04-20
forum: General Help
---

### Post by Saint_77 on 2010-04-20
Hi 

I get this error in my apache error.log file whenever i call the php mail() function.
I can send mail from the system and i have updated the php.ini files mail path to /etc/postfix
but i still get this error......any ideas anyone?

error.log  has this line after each call to php's mail() function
sh: /etc/postfix: Permission denied

Thanks

---

### Post by Untitled_No4 on 2010-04-20
I can't help you with Postfix since I've never used it with PHP. However, sendmail is a no-brainer with PHP, you only have to install it and you don't even have to edit any php files.

Install by running
```
sudo aptitude install sendmail
```
or from your favourite package manager. You will most likely have to undo all changes you have made to php configuration files.

---

### Post by Saint_77 on 2010-04-20
Thanks for the info but it will have to be postfix as the java applications and others currently make use of it (and its working) its only php that seems to not be able to make use of it.
Any ideas???

---

### Post by Untitled_No4 on 2010-04-20
Is /etc/postfix a directory or a file?
If it's a directory then this is why permission is denied -- you cannot execute a directory.

I found this and I hope it helps: [http://www.n8williams.com/devblog/php/using-the-mail-function-in-php-with-postfix-on-linux](http://www.n8williams.com/devblog/php/using-the-mail-function-in-php-with-postfix-on-linux)

---

### Post by Saint_77 on 2010-04-20
Thanks alot....this fixed it.
I updated my php.ini files to point to
sendmail_path = /usr/sbin/sendmail -t -i
and now the error is gone.

Thanks again.

---

### Post by ethand320 on 2011-05-19
doesn't sendmail have to be uninstalled to even use postfix? i am still having issues

---


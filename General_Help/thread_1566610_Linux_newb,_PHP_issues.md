---
title: "Linux newb, PHP issues"
date: 2010-09-02
forum: General Help
---

### Post by FirebornX on 2010-09-02
Hi, I'm new to Linux in general and I've been trying to setup a web development server with Ubuntu.

Having some trouble getting PHP to work properly though.

When I call phpinfo() for example I get the error:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0
Fatal Error: Unknown: Failed opening required '/var/www/phpinfo.php' (include_path='/usr/lib/php5/includes/') in Unknown on line 0

The odd thing is I can run phpmyadmin fine and it sits in /var/www/pma/

I'm not sure if it's a configuration error with php or apache or if it's a permission error or both.

any help is much appreciated.
Thanks!

---

### Post by Barrucadu on 2010-09-02
What permissions does /var/www/phpinfo.php have?

---

### Post by FirebornX on 2010-09-03
I figured out why this was occuring.

Seems that after editing my php files with netbeans it would change the permissions of the file when it FTP the changed file to the server.
There was an option in netbeans to "preserve remote file permissions" that fixed the problem.

Although new files created by netbeans have 000 permissions on them so I have to chmod those manually. Not sure how to fix that.

---


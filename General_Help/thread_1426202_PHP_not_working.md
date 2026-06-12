---
title: "PHP not working"
date: 2010-03-10
forum: General Help
---

### Post by WeaponsTheyFear on 2010-03-10
Hello all,
I just isntalled LAMP using tasksel and have a problem.  Whenever I try to access a page (aside from phpmyadmin, that works well), I get this error...

```

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

```

I have restarted the computer, restarted apache, etc and still nothing.  When I first installed, phpmyadmin was inaccessible, so I ran some command in terminal which apparently created a symlink between phpmyadmin in the user/share dir to the /var/www dir, and curious if this is the problem.

I have no clue how to remove this symlink if this is the case, and have phpmyadmin working now due to install using sudo apt-get install phpmyadmin.

Can anyone help me with this?

---

### Post by mavl4219 on 2010-03-10
Hi.

You remove symlink with the unlink command, and regarding your "Permission denied" problem: can you print out the output of ls -la /var/www? Mine looks like this:

drwxr-xr-x  2 root root 4096 2010-01-25 20:58 .
drwxr-xr-x 16 root root 4096 2010-01-25 20:54 ..
-rw-r--r--  1 root root   21 2010-01-25 20:58 index.php

---


---
title: "Cannot uninstall phpmyadmin"
date: 2006-02-15
forum: General Help
---

### Post by glave on 2006-02-15
I'm having a bit of trouble trying to move over to php5, the major problem is phpmyadmin refuses to cooperate. Trying to remove it, I get the following:
```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 24532 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Googling didn't seem to reveal anything to my immediate attention, so I'm kinda lost.

---

### Post by MasJ on 2006-02-15
A good thing to do would be search these forums. You'll get an answer to your question faster than Google. And probably the correct answer. I have this thread to recommend:

[http://www.ubuntuforums.org/showthread.php?t=127345](http://www.ubuntuforums.org/showthread.php?t=127345)

Please do search next time before posting a new thread.

---

### Post by glave on 2006-02-15
Kudos, that got it working. I had to adjust a permission on /var/lib/php5 after getting it installed, but that's a whole of can of worms.

Thanks for the pointer to the thread!

---


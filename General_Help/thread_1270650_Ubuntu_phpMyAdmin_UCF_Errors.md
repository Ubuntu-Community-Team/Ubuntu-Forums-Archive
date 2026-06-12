---
title: "Ubuntu phpMyAdmin UCF Errors"
date: 2009-09-19
forum: General Help
---

### Post by LeonBlade on 2009-09-19
Hello everyone,

I just was installing phpMyAdmin "officially" with a package and I got this error:

```

dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

```

Can someone tell me what I have to do?

ALSO, where do I go on my server to access it?
[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) ?

---

### Post by LeonBlade on 2009-09-19
```
/usr/share/phpmyadmin
```

I know that the files are there, but I think that the error I'm getting might be stopping it from working.

---

### Post by LeonBlade on 2009-09-20
I configured Apache so that it would show phpMyAdmin, but now I got this error trying to log in:
```
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

---

### Post by LeonBlade on 2009-09-21
I configured phpMyAdmin so I can log in now, I had to add a line to the apache config file even though the documentation said Jaunty would handle that for me but...

I'm sure that UCF error is still there, does anyone know how I can handle that?

---

### Post by LeonBlade on 2009-09-22
Anyone know what's wrong here?

---

### Post by LeonBlade on 2009-09-23
Should I just give up?

---


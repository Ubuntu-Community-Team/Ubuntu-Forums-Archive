---
title: "how to make ExecCGI on in /var/www/ ?"
date: 2009-11-23
forum: General Help
---

### Post by abhilashm86 on 2009-11-23
i'm running perl scripts, its giving this error in log, i don't know how to set ExecCGI option, please help.........
```
[Mon Nov 23 13:00:30 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 13:00:33 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
[Mon Nov 23 13:02:40 2009] [notice] caught SIGTERM, shutting down
[Mon Nov 23 13:02:41 2009] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Nov 23 13:02:41 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
[Mon Nov 23 13:02:50 2009] [error] Options ExecCGI is off in this directory/var/www/pgm2.pl
```

---

### Post by Prodigal Son on 2009-11-23
```
Options +ExecCGI
```

Add it to your Apache configuration file for the directory you are working in ( /var/www ).

---


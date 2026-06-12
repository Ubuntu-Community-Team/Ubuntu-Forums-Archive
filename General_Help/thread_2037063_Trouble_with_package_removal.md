---
title: "Trouble with package removal"
date: 2012-08-03
forum: General Help
---

### Post by mjh1972 on 2012-08-03
Hi, I've gone through several tutorials on removing broken packages, but I can't seem to get it. I'm on 10.04 and here is the error message I'm getting. Thanks in advance.

sudo dpkg --force all --remove gforge-plugin-mediawiki
(Reading database ... 201589 files and directories currently installed.)
Removing gforge-plugin-mediawiki ...
DBI connect('dbname=gforge','gforge',...) failed: FATAL:  Ident authentication failed for user "gforge" at /usr/share/gforge/lib/include.pl line 35
Uncaught exception from user code:
    Error while connecting to database:  at /usr/share/gforge/lib/include.pl line 37.
 at /usr/share/gforge/lib/include.pl line 37
    main::db_connect called at /usr/share/gforge/bin/unregister-plugin line 15
dpkg: error processing gforge-plugin-mediawiki (--remove):
 subprocess installed pre-removal script returned error exit status 255
Errors were encountered while processing:
 gforge-plugin-mediawiki

---

### Post by cortman on 2012-08-03
Please post output of

```
cat /usr/share/gforge/lib/include.pl
```

just in case there's some obviously corrupted characters in it or something simple.

---


---
title: "Two Problems"
date: 2006-02-15
forum: General Help
---

### Post by thaldyron on 2006-02-15
Hello!

1. Problem: I accidently changed the password for the mysql user debin-sys-maint. To make it possible for mysqlcheck to log in automatically again, I changed the password value in /etc/mysql/debian.cnf to the encrypted value I get with "select password from mysql.user". Unfortunately this doesn't solve the problem and I still get

```
/usr/bin/mysqlcheck: Got error: 1045: Access denied for user: 'debian-sys-maint@localhost' (Using password: YES) when trying to connect

```


2. How can I fix the following?
```

Feb 15 18:02:06 gatekeeper postfix/local[15798]: warning: database /etc/aliases.db is older than source file /etc/aliases

```

---

### Post by Prospero2006 on 2006-02-15
This is from my slackware distribution:
It might help with question #2.
#
#       @(#)aliases     8.2 (Berkeley) 3/5/94
#
#  Aliases in this file will NOT be expanded in the header from
#  Mail, but WILL be visible over networks or from /bin/mail.
#
#       >>>>>>>>>>      The program "newaliases" must be run after
#       >> NOTE >>      this file is updated for any changes to
#       >>>>>>>>>>      show through to sendmail.
#

---

### Post by thaldyron on 2006-02-15
Ok thanks, that seems to have fixed problem 2. :) 
Now problem 1 remains.

---


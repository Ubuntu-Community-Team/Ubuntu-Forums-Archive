---
title: "Installing mysql-server 4 on 10.04"
date: 2010-05-07
forum: General Help
---

### Post by Gimpyfuzznut on 2010-05-07
I'm pulling my hair out here. I'm trying to install mysql-server 4.1 on 10.04. Yes I know 4.1 is way out of date but I need to use it for work (our application only supports 4.1). 

I changed the repos to dapper universe but it still doesn't seem to let me install. I had the same problem on 9.10 but I can't exactly remember how I resolved the issue. 

Can anyone help me out here?

```
The following packages have unmet dependencies:
  mysql-server-4.1: Depends: mysql-common (>= 4.1.15-1ubuntu5) but it is not installable
                    Depends: mysql-client-4.1 (>= 4.1.15-1ubuntu5) or
                             mysql-client (>= 4.1.15-1ubuntu5)
                    Depends: libdbi-perl but it is not installable
                    Depends: libmysqlclient14 but it is not going to be installed
                    Depends: libreadline5 (>= 5.1) but it is not installable
E: Broken packages

```

---

### Post by Gimpyfuzznut on 2010-05-11
Help please!

---

### Post by gmargo on 2010-05-11
What do you want help with?  You already know that you can't install things from Dapper onto Lucid and expect it to work.  4.1 was obsolete even in Dapper.  If you really must have that version, your best bet is to compile it from source.  Even that may be difficult.

---


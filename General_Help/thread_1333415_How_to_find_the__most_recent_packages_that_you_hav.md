---
title: "How to find the  most recent packages that you have installed ?"
date: 2009-11-21
forum: General Help
---

### Post by uncle-c on 2009-11-21
Hi,
I know that you can list all the packages installed on you system by using the following command
```

dpkg --get-selections
```

However, is there a way of listing the packages that you have installed in reverse chronological order i.e. most recent package installed first ?
The reason is that I have been installing lots of software using apt-get but would like to have an idea of what my recent activity has been.
Is there a config /database file which show which package was installed and the date it was installed on ?

EDIT:

Silly me, dpkg log files are kept in /usr/var/log/ !!!

c

---


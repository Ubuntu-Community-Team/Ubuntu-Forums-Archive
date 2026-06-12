---
title: "Can't stat /lib/x86_64-linux-gnu"
date: 2010-11-18
forum: General Help
---

### Post by bluesquall on 2010-11-18
I was tracking down some other library linking problems when I noticed this issue:
[INDENT]~$ sudo ldconfig -v
/sbin/ldconfig.real: Can't stat /lib/x86_64-linux-gnu: No such file or directory
/sbin/ldconfig.real: Can't stat /usr/lib/x86_64-linux-gnu: No such file or directory
[/INDENT]
These are related to the file /etc/ld.so.conf.d/x86_64-linux-gnu.conf with the contents:
[INDENT]
# Multiarch support
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu
[/INDENT]
I believe that file was on my new install in the beginning.

This doesn't seem to be causing any problems right now, but I would like to figure out what package is associated and clean this up.

Current configuration:
10.10 Maverick (64-bit) server, running headless

---

### Post by Amabele on 2012-05-28
I also have the same issue.
It would be nice to know which package needs to be uninstalled to get rid of this.

thanks.

---

### Post by oldos2er on 2012-05-28
Closed, please start a new thread for your question.

---


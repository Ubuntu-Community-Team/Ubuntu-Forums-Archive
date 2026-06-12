---
title: "Could not open the following files:"
date: 2010-02-16
forum: General Help
---

### Post by sisyphus1978 on 2010-02-16
I'm trying to fix a problem I've had for a few weeks. Opening system log gives me: Could not open the following files:
> /var/log/apport.log.1: Error stating file '/var/log/apport.log.1': No such file or directory
/var/log/auth.log.1: Error stating file '/var/log/auth.log.1': No such file or directory
/var/log/daemon.log.1: Error stating file '/var/log/daemon.log.1': No such file or directory
/var/log/kern.log.1: Error stating file '/var/log/kern.log.1': No such file or directory
/var/log/lpr.log.1: Error stating file '/var/log/lpr.log.1': No such file or directory
/var/log/user.log.1: Error stating file '/var/log/user.log.1': No such file or directory
/var/log/debug.1: Error stating file '/var/log/debug.1': No such file or directory
/var/log/messages.1: Error stating file '/var/log/messages.1': No such file or directory
/var/log/jockey.log.1: Error stating file '/var/log/jockey.log.1': No such file or directory
/var/log/jockey.log: Error stating file '/var/log/jockey.log': No such file or directory
/var/log/apport.log: Error stating file '/var/log/apport.log': No such file or directory
/var/log/syslog.1: Error stating file '/var/log/syslog.1': No such file or directory
/var/log/fontconfig.log: Error stating file '/var/log/fontconfig.log': No such file or directory
/var/log/boot: Error stating file '/var/log/boot': No such file or directory
/var/log/bootstrap.log: Error stating file '/var/log/bootstrap.log': No such file or directory
Yesterday I rm -r /var/log/ to attempt to fix it (hoping the files would rebuild themselves) but it doesn't seem to have worked entirely.

Any ideas? Thanks.

---

### Post by rnerwein on 2010-02-16
hi
don't be afraid about those messages. the files are only stated not opened. they come from the log rotation. there must be a data base with those names ( i don't know where ). 
but the "current log files will be create or if present appended on boot". have a look at your /var/log and you will see that there are new files created.
ciao

---


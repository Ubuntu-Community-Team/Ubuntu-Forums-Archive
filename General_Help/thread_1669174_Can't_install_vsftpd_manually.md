---
title: "Can't install vsftpd manually"
date: 2011-01-17
forum: General Help
---

### Post by rozo on 2011-01-17
Hello,

I have to install vsftpd on several pc's that don't have internet connection, so I download the package and tried to install it the way described in INSTALL, but it doesn't work, I get those errors:
install: accessing '/usr/local/man/man8/vsftpd.8': Not a directory
install: accessing '/usr/local/man/man5/vsftpd.conf.5': Not a directory
So I tried to copy those files manually as it is described in [www.thegeekstuff.com/2010/11/](www.thegeekstuff.com/2010/11/)**vsftpd**-setup/
and to manually set the startup service:
update-rc.d vsftpd defaults
Everything looks fine, I can start vsftpd manually and it works, but if I start the pc the vsftpd service isn't running.
Anyone knows how to do it properly or what am I doing wrong?

Marcin

---


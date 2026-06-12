---
title: "Access external hard drive via FTP?"
date: 2009-12-30
forum: General Help
---

### Post by aceplayer97 on 2009-12-30
Is it possible for me to build a FTP server on one computer which has an external hard drive attached to it and then connect to that one computer from my laptop and access the files on the external hard drive?:confused:

---

### Post by StuartN on 2009-12-30
> **aceplayer97 said:**
> Is it possible for me to build a FTP server on one computer which has an external hard drive attached

I am not sure that you would want to install and enable an FTP server just to share a directory or drive, but you could install ftpd or the more secure vsftpd and configure the settings in /etc/ftpd.conf or /etc/vsftpd.conf - see [http://manpages.ubuntu.com/manpages/jaunty/en/man5/vsftpd.conf.5.html](http://manpages.ubuntu.com/manpages/jaunty/en/man5/vsftpd.conf.5.html) for some details.

If you are literally just sharing data across your internal network, then enable sharing on the root directory. You can do this in Nautilus by right-clicking the directory and selecting Sharing Options. The first time around you might be asked to install part of Samba file sharing.

---


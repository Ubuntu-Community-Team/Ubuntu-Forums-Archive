---
title: "Looking for Easy to Set up FTPS Server"
date: 2011-08-15
forum: General Help
---

### Post by jhall1990 on 2011-08-15
Hello I recently moved my laptop to Ubuntu and I used to host an FTPS server on it. I used Filezilla server, which unfortunately is not available for Ubuntu at the moment. I have tried a few Linux ftp server offerings (vsftpd, proftpd and pureftp) and neither of these was as easy and intuitive to configure. Is there any FTP server software that is easy to configure more like Filezilla, a GUI would be nice if possible.

---

### Post by tredegar on 2011-08-15
Try [woof]("http://www.linux.com/archive/feature/60098"). It's *very* easy to use.

---

### Post by Lars Noodén on 2011-08-15
I would recommend moving to SFTP instead.  The package OpenSHH-server will give you that and it works out of the box.  Filezilla, Nautilus and many other support SFTP.  It's simpler.

---

### Post by jhall1990 on 2011-08-15
I know of SFTP but I do no now know how to change the directory that I can put into when I login, is there any way to change it away from my home directory?

---

### Post by aeiah on 2011-08-15
> **jhall1990 said:**
> I know of SFTP but I do no now know how to change the directory that I can put into when I login, is there any way to change it away from my home directory?

set up another user account and have that as the one people log on to

---


---
title: "ftp Directory"
date: 2010-02-09
forum: General Help
---

### Post by adeelm on 2010-02-09
Hi everyone,

                   I have installed vsftpd on ubuntu 9.04 and can access it over my lan from different users. But when ever I login to ftp with a specific user it goes to its home directory. I do not want them to go to their home directory. 

Can someone tell me that how can I change it so that who ever logins, should go to the ftp directory not the home directory.

Thanks

Adeel

---

### Post by gmargo on 2010-02-09
**local_root** option?

[SIZE=2][http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)
[/SIZE]

---


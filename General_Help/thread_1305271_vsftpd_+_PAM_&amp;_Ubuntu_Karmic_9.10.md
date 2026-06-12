---
title: "vsftpd + PAM &amp; Ubuntu Karmic 9.10"
date: 2009-10-29
forum: General Help
---

### Post by ericab on 2009-10-29
im having problem here

i *just* upgraded from 9.04 jaunty to 9.10 karmic final, and i cant login to my ftp server anymore!

i get the error:

Oct 29 14:46:41 lnx-serv vsftpd: pam_unix(vsftpd:auth): check pass; user unknown

Oct 29 14:46:41 lnx-serv vsftpd: pam_unix(vsftpd:auth): authentication failure; logname= uid=0 euid=0 tty=ftp ruser=eric rhost=192.168.1.100

from /var/log/auth.log



i find that if i comment out:

# Standard behaviour for ftpd(.
# auth required pam_listfile.so item=user sense=deny file=/etc/ftpusers o$

the above, from /etc/pam.d/vsftpd, that i can login again.

what has changed ?

---


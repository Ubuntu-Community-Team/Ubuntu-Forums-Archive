---
title: "home dirctory on a different server in AD enviorment?"
date: 2012-03-01
forum: General Help
---

### Post by Beandip408 on 2012-03-01
i have been binding my ubuntu servers to our Windows Server 2008r2 Active Directory and it has been working fine. 
in my /etc/samba/smb.conf file i specify a home folder for each user like this:
template homedir = /home/%D/%U

will a home directory work being stored on a different server?

obviously i will have to auto-mount that server, but how to i get that setup for each user?
is it as easy as doing this?:
template homedir = /UbuntuHomeServer/home/%D/%U

or do i need to do something special?

---


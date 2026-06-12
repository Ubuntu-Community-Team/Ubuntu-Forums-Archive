---
title: "Filezilla error accessing a secure ftp"
date: 2012-05-31
forum: General Help
---

### Post by satish_j on 2012-05-31
A fresh install of Filezilla from software centre in Precise pangolin and could not connect to a secure remote ftp server.It gives foll error on trying to establish a connection:
[B]Error: GnuTLS error -12: A TLS fatal alert has been received.
Error: Could not connect to server[/B]
Any ideas how to resolve it.Firewall is de-activated,so this is not port related problem..

---

### Post by satish_j on 2012-05-31
googled and found that this may be related to ftp server iam connecting to.There is some setting for vsftpd(if it is used on that server)to add ssl_ciphers=HIGH in its conf file.
Since i do not have control over the ftp server iam connecting to,i will try downgrading the filezilla version at my end and check,since that is also a workaround reported by someone.

---


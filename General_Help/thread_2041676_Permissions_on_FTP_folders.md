---
title: "Permissions on FTP folders"
date: 2012-08-13
forum: General Help
---

### Post by darkmediator on 2012-08-13
Hi,
  
  I'm having directory "documents" in /var/ftp/pub.

  It would only have upload rights not download, delete or change, read or write. Only root has the right to do every thing on these ftp .

Please tell me the necessary permissions I need to give and also the acl settings.

I have set 222. But I'm not able to make directories. Please help

---

### Post by spjackson on 2012-08-13
Which ftp server are you using?

---

### Post by darkmediator on 2012-08-13
vsftpd => CentOS 5

---

### Post by JKyleOKC on 2012-08-13
Try 733 instead of 222. It won't hurt to give the owner read permission also, since things are owned by root, but 333 should also work. Directories need the "execute" bit set in order to be browseable!

---

### Post by darkmediator on 2012-08-13
Thanx a lot, that was a superb alternative! :)

---


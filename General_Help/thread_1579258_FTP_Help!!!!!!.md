---
title: "FTP Help!!!!!!"
date: 2010-09-21
forum: General Help
---

### Post by icee1222 on 2010-09-21
I am trying to access a mounted secondary drive through FTP, and when I try to connect to it I am not able to see any of its contents. Any suggestions? I am using Gadmin-proftp to configure. I can point it to any other folder on the main drive and see it perfectly.

---

### Post by bodhi.zazen on 2010-09-21
Sounds as if FTP is working, my guess is a permissions problem on the server.

What are the ownership and permissions of the shared drive ?

Also, ftp is probably OK on a LAN, but over the internet consider ssh (scp / sftp).

---


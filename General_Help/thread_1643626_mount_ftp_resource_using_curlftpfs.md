---
title: "mount ftp resource using curlftpfs"
date: 2010-12-12
forum: General Help
---

### Post by pls on 2010-12-12
Hi! 
I have wireless router and USD HDD connected to it. And now want to make access to it (from my laptop) using ftp. I used curlftpfs to mount HDD.
The problem:
while coping files from laptop to remote USB HDD via ftp (using curlftpfs) I got such an error:

> "Cannot close target file "/directory/filename.extension" Input/output error (5)"

But! File copies successfully, and works perfectly!

How can I avoid such a messages?

---

### Post by pls on 2010-12-14
what's wrong?! nobody knows how to fix it???

---

### Post by pls on 2010-12-21
SOLVED by downgrading to curlftpfs 0.9.1

---


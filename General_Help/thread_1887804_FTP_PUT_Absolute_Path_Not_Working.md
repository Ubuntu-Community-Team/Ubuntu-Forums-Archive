---
title: "FTP PUT Absolute Path Not Working"
date: 2011-11-27
forum: General Help
---

### Post by greenpin on 2011-11-27
I am trying to FTP files from an Ubuntu Server 11.10 to another Unix server using the CLI FTP client. I can 'put example.txt' successfully while CD'ed to the file's local current directory, however, I can not 'put /home/username/example.txt'.

Why can I not use the absolute path to the file?

---

### Post by CryptAck on 2011-11-27
I usually use lftp over normal FTP, I find it to work better.

---

### Post by greenpin on 2011-11-30
As a fairly new Linux CLI user, I can't thank you enough for the lftp suggestion! It does exactly what I wanted ftp to do. \\:D/

---


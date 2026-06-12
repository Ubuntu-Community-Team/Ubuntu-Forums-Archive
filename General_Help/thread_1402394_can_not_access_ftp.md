---
title: "can not access ftp"
date: 2010-02-09
forum: General Help
---

### Post by adeelm on 2010-02-09
hi evryone,

         I have installed vsftpd on Ubuntu 9.04 and configured it. but i can not access the ftp. when  anonymous was yes i could access the ftp. Now that I have changed to anonymous_enable=NO, it prompts for username and password. I have also created the vsftpd.chroot_list file in /etc/vsftpd.chroot_list but still I am not able to access the ftp.

Need you help in this manner. I have attached the vsftpd configuration file.

Adeel

---

### Post by mushwars on 2010-02-09
Here is my working config, edit it to work for you 

[http://pastebin.com/m66cbbf9f](http://pastebin.com/m66cbbf9f)

---


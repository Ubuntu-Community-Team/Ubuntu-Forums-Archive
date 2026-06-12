---
title: "Connect to Ubuntu"
date: 2012-03-13
forum: General Help
---

### Post by mbm1234 on 2012-03-13
Hello, I have three computers, the first one have Windows 7, the second one have Linux Ubuntu, and third one have Linux Open Suse, Most of the time I am working with Windows computer, I can connect from Windows to Linux Open Suse using a program call WinSCP and Putty(use ssh(Secure SHell)), WinSCP(use sftp(Secure File Transfer Protocol)) allow me to copy, move and so on from Windows to Linux Open Suse or from Linux Open Suse to Windows, With the program Putty I give command to the Linux Open Suse, these services that Linux Open give me make my work easy and faster, but Linux Ubuntu does not allow me to connect like I do with Linux Open Suse, is it possible to enable these services in Linux Ubuntu?, thanks in advance.

---

### Post by Paqman on 2012-03-13
To SSH into your Ubuntu box you'll need to install [openssh-server]("apt:openssh-server"). For FTP you'll want [vsftpd]("apt:vsftpd").

[More on SSH]("https://help.ubuntu.com/community/SSH")
[More on FTP]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html")

---

### Post by mbm1234 on 2012-03-14
Hello Paqman, Thankyou.

---


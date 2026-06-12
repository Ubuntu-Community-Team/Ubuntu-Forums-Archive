---
title: "ftp server"
date: 2010-08-27
forum: General Help
---

### Post by safee1248 on 2010-08-27
how do i set up a ftp sever?

---

### Post by chrisinspace on 2010-08-27
Instead of traditional FTP, which is not secure and is quite dated, set up SSH.  You can do file transfer over SSH and it is encrypted.

---

### Post by chrisinspace on 2010-08-27
I found you a pretty good [guide to setting up SSH]("http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/").  For more information check out the [Ubuntu Documentation]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html") SSH page.

Once you have SSH set up on your server, you can use any FTP client that supports SFTP (SSH File Transfer Protocol).  I use [Filezilla]("http://filezilla-project.org/").  In the Filezilla site manager, set up a new site with the following fields:

Host: Your public DNS name or IP address
Port: 22 is the default, but you can change the port SSH listens to on your server if you want.
Logon type: Normal
User: valid username on our SSH server
Password: password for that user account

---


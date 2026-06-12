---
title: "FTP Server"
date: 2006-03-26
forum: General Help
---

### Post by anandrd on 2006-03-26
I have set up a secure FTP server using proFTPD and I can transfer files using sftp (from linux machines) or using FileZilla (for windows machine.) I wanted to ask if it is possible to set up some service so that one can access files using any web browser (by going to [ftp://myIP)](ftp://myIP)). Additionally, it would be great if I could setup a password to do this.

---

### Post by astyanax on 2006-03-26
I don't have an FTP server on my machine and I don't recommend using one.  An sftp is much more secure, but if you want an FTP server, you can use the ftp daemon.

Install the ftp daemon:
```
sudo apt-get install ftpd

```
You can use this wiki to configure the server:
[http://www.nslu2-linux.org/wiki/HowTo/SetupFtpd](http://www.nslu2-linux.org/wiki/HowTo/SetupFtpd)

---


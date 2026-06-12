---
title: "Unable to set anonymous privileges. . .?"
date: 2011-06-26
forum: General Help
---

### Post by rLLZORS on 2011-06-26
Hi, I'm pretty much a linux noob and I've managed to set up a ftp server with gadmin-proftpd, i need to access the "Downloads" folder from the "Home Folder" but it won't allow me, I've set up the login fine, I just can't get it to show the directory.

Status:    Connecting to 
Status:    Connection established, waiting for welcome message...
Response:    220 My FTP Server
Command:    USER rLLZORS
Response:    331 Password required for rLLZORS
Command:    PASS ********
Response:    530-Unable to set anonymous privileges.
Response:    530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server

---

### Post by noah++ on 2011-06-27
Dunno; but it demonstrates one of the reasons I always use SFTP instead of FTP. All I need to make an SFTP server work is OpenSSH daemon and a normal user account. No fussing with application-specific configurations.

---


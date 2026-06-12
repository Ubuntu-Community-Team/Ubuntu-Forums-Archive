---
title: "vsftpd configurations"
date: 2011-12-12
forum: General Help
---

### Post by louis vitton on 2011-12-12
Hey guys,

i want to create a ftp server which will allow access to /var/www and allow me to create directories and upload and download files from here. I want this to be use filezilla as my ftp client to use for this. Currently my FTP server i have configured will allow me to full access to the home dir of the user but not allow me to upload or make directories in the /var/www directory.

Cheers for the help

I am using the ubuntu 11.04 version also. Cheers.

---

### Post by Lars Noodén on 2011-12-12
First you need to set the permissions for [font=Courier New]/var/www[/font] so that you can write or change it.

```

sudo addgroup webmasters

sudo gpasswd --add louisv  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

Then I would recommend retiring good old [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and using SFTP instead.  You can get it by installing the packgage [openssh-server](apt://openssh-server).  No further configuration is needed.

---

### Post by louis vitton on 2011-12-12
> **Lars Noodén said:**
> Then I would recommend retiring good old [FTP]("http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/") and using SFTP instead.  You can get it by installing the packgage [openssh-server]("apt://openssh-server").  No further configuration is needed.

openssh is already installed i use it to connect to the server via ssh putty.
Sorry noob question but how can i FTP using openssh if i dont install vsftpd? 

Also how can i get filezilla to connect to the openssh and use that for ftp?

Cheers

---

### Post by Lars Noodén on 2011-12-12
The trick is to not use FTP at all.  For file transfers you have SFTP instead, which unlike FTP is secure.  FileZilla supports SFTP.  When you connect using FileZilla, there is a "protocol" option, set that to SFTP.

---

### Post by louis vitton on 2011-12-12
> **Lars Noodén said:**
> The trick is to not use FTP at all.  For file transfers you have SFTP instead, which unlike FTP is secure.  FileZilla supports SFTP.  When you connect using FileZilla, there is a "protocol" option, set that to SFTP.

Thank you i have connected and it works great.
I shall remove all the old ftp now. 

Cheers for the help.

---


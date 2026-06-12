---
title: "ftp using filezilla client"
date: 2011-12-07
forum: General Help
---

### Post by gacy on 2011-12-07
Hello everybody
I just installed ubuntu 11.10 and now I am trying to transfer some files from a PC running windows 7. To transfer the files from the windows machine I use the ftp client filezilla version 3.5.2, but when I try to make a connection to the ip address of the ubuntu 11.10 machine I get the error message "ECONNREFUSED - Connection refused by server". Is there some kind of configuration I need to do on the ubuntu machine in order to allow me to ftp?

Thank you all!

---

### Post by Lars Noodén on 2011-12-07
There has to be a corresponding server on the remote machine to match the client you are trying to use locally.  However, it is time to [stop using FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  

SFTP is a secure replacement.  FileZilla supports SFTP and you can put a SFTP server on your other machine by installing the package OpenSSH-Server.  That will give you a configured and working SFTP server.

---

### Post by seawolf167 on 2011-12-07
As mentioned above, your Windows 7 machine will need to run a server version to serve the files to the client computer, your linux box. See [their website ]("http://filezilla-project.org/")for the server download for your Windows 7 machine. Download, install, run, then you should be able to connect from your linux box.

---

### Post by Lars Noodén on 2011-12-07
Or you can put the server on the Linux box and connect that way.  It's easier and safer.

---

### Post by gacy on 2011-12-08
:D
Thank you both for your help! 
I installed openssh server and now sftp works from filezilla.
 
Thank you):P

---

### Post by kanishkdudeja on 2011-12-08
Please mark the thread as solved so that others don't waste their time looking into it.

---


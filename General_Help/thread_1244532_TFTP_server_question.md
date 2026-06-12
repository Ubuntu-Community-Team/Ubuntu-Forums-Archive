---
title: "TFTP server question"
date: 2009-08-19
forum: General Help
---

### Post by rickyble on 2009-08-19
I have set up a tftp server on an ubuntu 8 server.  My Cisco gear is saving the configs to this tftp server.  My question is this... I have a user called Cisco as the tftp user.  But I want the files as they are written from the switch/router by the cisco user to be automatically included with rw for a group called cisco-g.  I have samba running for a group of admin users and want them to have rw access to these files so they can modify them and then save them and have them tftp back down to the switch/router with changes if needed.  The group has rights to the directory but as tftp writes the files to the directory the cisco-g has no rights to the newly written files.  Can anyone help?

---

### Post by HermanAB on 2009-08-19
Note that for security reasons most TFTP servers will refuse to do anything if the files and directory it points to is Read Write.  You need to set it as Read Only.  Read the appropriate man page for your TFTP server for details.

---

### Post by rickyble on 2009-08-20
Actually I have been reading and searching for days.  I have changed my user in the config files of the tftp server to myself and which causes the incoming files then to be written so I can accomplish this exact task but I want it to be for a specific group. I have read in several places that the rights can not be anything except read only but I have found it works with full rights.  So my question is not will it work but simply how to make the files that are being written fully rw for a specific group...ie cisco-g.  How would it be done in any directory say an ftp server.  I use the same method.  I looked at the profile script but Im to much of a newbie to muck with that.  I thought about running a cron job to change the files but that really seems so clumsy.

---

### Post by rickyble on 2009-08-20
Yes just look at ftp.  How can I accomplish the same thing using ftp.  All files uploaded into my /mnt/ftp/FTP-shared/upload directory should be rw for cisco-g users.  Hows that.  Ill just use ftp instead of tftp

---


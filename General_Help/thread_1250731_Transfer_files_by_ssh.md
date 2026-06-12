---
title: "Transfer files by ssh?"
date: 2009-08-26
forum: General Help
---

### Post by Kdar on 2009-08-26
I have Ubuntu 9.04.

Right now I am able to connect to a server in my University Unix lab to be able to see files in home directory of my account.
I use this: ssh -Y [email]username@machine-name.eng.uah.edu[/email]

How can I transfer files from my laptop to there? (by terminal or some kind of software is fine too).

---

### Post by tuxxy on 2009-08-26
Can you not FTP into it, try sftp command at prompt.

---

### Post by renkinjutsu on 2009-08-26
if you have ssh, then you should be able to connect through sftp

go to:
Places -> Connect to Server
select sftp on the dropdown menu and fill in all the information


alternatively, you can use the terminal to transfer files through scp which works like this

scp -P PORT USER@HOSTNAME:/path/to/file/or/directory USER@HOSTNAME:/path/to/save

man scp for more information

---

### Post by zubin71 on 2009-08-26
use scp

read this 
[http://www.hypexr.org/linux_scp_help.php](http://www.hypexr.org/linux_scp_help.php)

---

### Post by jerome1232 on 2009-08-26
Places -> Connect to Server -> SSH

This will put the share on you desktop and you can browse it with nautilus. Pretty sure it's using scp.

---


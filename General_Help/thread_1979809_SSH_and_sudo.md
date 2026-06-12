---
title: "SSH and sudo"
date: 2012-05-14
forum: General Help
---

### Post by beginner_ on 2012-05-14
Hi all,

I would like to connect to a Lubuntu 12.04 installation with SSH/SFTP (using WinSCP) and have sudo privileges for editing files. The thing is that I successfully set this up for Ubuntu Server and I just repeated the steps for Lubuntu but it does not work. When connecting to Lubuntu I get following error:

*Cannot initialize SFTP protocol. Is the host running a SFTP server?*

In WinSCP, one must set the setting *Environment->SFTP* to

*[FONT=&quot]sudo /usr/lib/openssh/sftp-server[/FONT]*  

for this to work. I can leave it at default value and then connection works however without sudo privilege.

For this to work I created a file in etc/sudoers.d with following content:

[FONT=&quot]userName ALL=NOPASSWD: /usr/lib/openssh/sftp-server[/FONT]

---


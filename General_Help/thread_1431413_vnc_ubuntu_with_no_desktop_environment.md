---
title: "vnc ubuntu with no desktop environment"
date: 2010-03-16
forum: General Help
---

### Post by The Mishanator on 2010-03-16
i have a server that runs ubuntu 9.10 and with GNOME. my server is a pretty crappy machine and GNOME uses way too many resources. since it's in a different room, i use vnc to access it and ftp to change files. there is no problem with ftp and no desktop environment. however i do not know of a way to use vnc on this machine without GNOME or KDE or any other desktop environment.

is there a way to do this? such as a console based vnc server?
perhaps if there arent is there a different (better) way to do this?

---

### Post by Brandon Williams on 2010-03-16
If I understand, you're looking for a way to access the machine that doesn't use graphical applications, since the graphical apps require a lot of resources to run.

The typical way to access a server for administration, etc. is via ssh. 'sudo apt-get openssh-server' will set you up. If the server is accessible via the internet, you'll probably want to set up ssh for key-based authentication and maybe switch to a non-standard port.

---

### Post by asmoore82 on 2010-03-16
[SIZE="5"]Big +1[/SIZE] for SSH.

OpenSSH also provides sFTP which can totally replace FTP in a more secure manner.

You may want to check out the link in my signature.

---

### Post by The Mishanator on 2010-03-16
alright that is done. where are the config files?

---

### Post by Brandon Williams on 2010-03-17
View 'man sshd_config' to get details about the sshd config file. It will tell you the path and what the various settings mean.

---


---
title: "Samba is having an issue with install"
date: 2010-09-27
forum: General Help
---

### Post by vexoy on 2010-09-27
I am running Ubuntu 10.04

I have installed Samba by using the command:

sudo apt-get install samba

When it get to the end it has a issue:

Setting up samba (2:3.4.7~dfsg-1ubuntu3.2) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 2094
start: Job failed to start

I have been looking between a whole bunch of tutorials to try and install samba and it seems that the install of samba doesn't include the necessary things. Some say to do:

sudo smbpasswd -a USERNAME

Though that doesn't work, the terminal doesn't recognize the command. Some of them say to edit the smb.conf file but I can't find it and the directory /etc/samba/smb.conf doesn't exist.

I have no idea what the problem is, any help would be much appreciated!!!!

---


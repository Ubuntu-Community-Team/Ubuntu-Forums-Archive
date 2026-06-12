---
title: "Samba problem Ubuntu 11.10"
date: 2012-03-07
forum: General Help
---

### Post by robinasa on 2012-03-07
I have some problems with my samba installation.
I have tryed to remove samba and install again:

[HTML]Sudo apt-get remove samba[/HTML]
[HTML]Sudo apt-get remove --purge samba[/HTML]

and so tryed to install again from ubuntu desktop..

I got this message:

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 152644 files and directories currently installed.)
Unpacking samba (from .../samba_2%%3a3.5.11~dfsg-1ubuntu2.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up samba (2:3.5.11~dfsg-1ubuntu2.1) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 7734
start: Job failed to start
invoke-rc.d: initscript nmbd, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
Error in function: 
Setting up samba (2:3.5.11~dfsg-1ubuntu2.1) ...
start: Job failed to start
invoke-rc.d: initscript nmbd, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1


And i can`t install...


What to do?

---

### Post by robinasa on 2012-04-17
SOLVED:popcorn:

---

### Post by pirsl on 2012-04-19
How?

---


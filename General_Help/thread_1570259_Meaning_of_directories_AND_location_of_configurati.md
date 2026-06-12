---
title: "Meaning of directories AND location of configuration files"
date: 2010-09-07
forum: General Help
---

### Post by Robert R on 2010-09-07
Hi im  new to linux and using **Ubuntu 10.04 (Lucid)**
I would like to create a backup strategy that would allow for me to restore folders e.g.(/etc)
so in case my disk crashes i just restore these folders and restore **all current programs and setting and also user specific settings ** 
not the entire music or pictures folders i can do these backups manually anytime. 



Also i did some research and my did the following configuration upon installing ubuntu. 

14 GB SWAP SPACE
4.1 GB /
32 GB /USR
85 GB /HOME

Can someone please explain where settings are stored for programs where programs are stored and user settings this would be much help thanks in advanced. ):P

---

### Post by ezsit on 2010-09-07
The remastersys tool, available at [www.remastersys.com](www.remastersys.com), will make a bootable ISO image file of your entire system (BACKUP mode), or just the system and leave the user settings as default (DIST mode backup). The ISO must be smaller than 4.4GB, so backup your data separately. If you do not have too much in your /home folder (store your large files elsewhere), the BACKUP mode will do exactly what you want, plus give you a LiveDVD of your system you can run and reinstall at will.

Trying to backup programs and settings manually is almost pointless. There are Backup programs, just search the SOftware Center for Backup and you'll have a few choices.

---

### Post by Robert R on 2010-09-07
OK i understand but lets say i have spent hours installing a driver for my wireless nic and want to back that up specifically
 so i wont have to again even if my disk crash. Is there a way to know where these files or settings are stored. 
If u do know please tell.

---

### Post by gauravj on 2010-09-08
Yes, there certainly is.
Open synaptic package manager and right click on package name.
select properties. You will get a window with the installed file tab.

---

### Post by Robert R on 2010-09-08
WOW :D I see the light. Thanks guys.

---


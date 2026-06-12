---
title: "36 Gig of files wandering"
date: 2009-12-01
forum: General Help
---

### Post by Achilles124 on 2009-12-01
I have made a backup with the program Simple Backup. After some digging why my harddrive space was so full, I find out that it was caused by a backup in /var/backup. 

I went into gksudo nautilus and removed the backup. Rebooted my computer but my disk is still full.

I typed: **sudo du -h --max-depth=1 / | grep '[0-9]G\>'**

and I got:
> du: kan geen toegang krijgen tot `/home/ecmpeek/.gvfs’: Toegang geweigerd
56G	/home
8,3G	/usr
36G	/root
du: kan geen toegang krijgen tot `/proc/3557/task/3557/fd/3’: Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/3557/task/3557/fdinfo/3’: Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/3557/fd/3’: Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/3557/fdinfo/3’: Bestand of map bestaat niet

?????????????????
The 36 gig has been removed from /var/backup and then appears into the root folder. And I cannot find it anymore. What to do?

---

### Post by John Bean on 2009-12-01
It's probably in root's trash. If using a sudo Nautilus be careful to actually delete (shift+del) rather than just moving to trash (del).

---

### Post by Achilles124 on 2009-12-01
These are the files I find in root-trash:

> gedit.ecmpeek.3422700449
keyring-fX1oTX
libgksu-e23Xbt  
orbit-gdm   
pulse-P5DMZRi0LADb  
screenlets      
tracker-ecmpeek
gufw.pid
libgksu-BSmrEN
orbit-ecmpeek
orbit-root
pulse-PKdhtXMmr18n
ssh-RULcUq2837
virtual-ecmpeek.R6EQOB


The file is not there.

---

### Post by Achilles124 on 2009-12-01
btw, when running gksudo nautilus, I get an error message:

Details —  1: Verbinding maken met de sessie is mislukt: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

---

### Post by Achilles124 on 2009-12-01
Phew, got rid of that. Searched in the wrong place. I found it in:
.root/local/share/trash/files.

Thank you for answering, John Bean.

---

### Post by John Bean on 2009-12-01
My pleasure; been there, done that. It took me a while to get into the habit of using the shift key when deleting files in a sudo Nautilus session :-)

---


---
title: "Windos cannot access DVDs/CDs"
date: 2012-01-11
forum: General Help
---

### Post by BCopas on 2012-01-11
I have several DVD-ROM & CD-ROMs with research material. I have mounted and shared the drives. Also, I have created Samba shares of the folders. On Windows XP and Win7x64, I can see the shares but can not access any of the drives. I get: 
 
Windows cannot access [\\SERVER\dvd]("file://\\SERVER\dvd")
 
You do not have permission to access [\\SERVER\dvd]("file://\\SERVER\dvd"). Contact your network adminstrator to request access.
 
This is my first Linux install. PLEASE HELP!!! and THANKS IN ADVANCE!!!
 
Misc Info:
 - Ubuntu 11.10 64-bit sever with Ubunut Desktop
 - ASUS P5Q
 - Sony Optaric SATA DVD-ROM drives (5)

---

### Post by BCopas on 2012-01-12
Update - I installed SWAT and updated Admin Users and Read List entries to include my user account.  I can now access the one PATA CD-ROM, but none of the SATA DVD-ROMs.  Any suggestions?

---

### Post by BCopas on 2012-01-16
I found the problem - the DVDs could not be mounted via /etc/fstab.  Instead, I edited /etc/init.d/rc.local and added the mount commands.  On boot, the system mounts the DVDs to the directories I created.  After setting up the shares in Samba, my Windows computers are able to access the DVDs. :P

---


---
title: "Mounting windows file on logon"
date: 2010-02-02
forum: General Help
---

### Post by Tadeja on 2010-02-02
I have active directory users. User can log on with username/password from active directory in ubuntu. Users have their directory on Windows file server. 
They have read and execute rights on file on windows file server with same username and password from active directory(192.168.2.1/file/username for each user).
I want that user's directory on windows file server mount to /home/username/disk on logon for each user, which logon in ubuntu. 
Thankful for your answers.
Kind Regards!

---

### Post by Robster2 on 2010-02-02
The only thing I can suggest is that you install the NTFS configuration Tool

Applications>Add/Remove

Applications>Software Manager (Karmic)

Search for NTFS

Install

To run

System>Administration>NTFS Configuration Tool

See if you can find something there.  

If not you will need to change /etc/fstab don't know how - Sorry.

---


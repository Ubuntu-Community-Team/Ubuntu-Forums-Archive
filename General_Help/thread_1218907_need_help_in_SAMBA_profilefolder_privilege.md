---
title: "need help in SAMBA profile/folder privilege"
date: 2009-07-21
forum: General Help
---

### Post by rawrico on 2009-07-21
I need help on this type of file sharing settings
as the picture shown,
SHARED folder is are shared and must have ID to LOGIN for WRITABLE privilege,which mean "ADMIN"
VIDEO folder is inside the SHARED folder,of course "ADMIN" can access to rewrite this VIDEO folder, however, this VIDEO folder also shared to every user as like "GUEST", this user can only VIEW the file and folder,not rewrite privilege

ADMIN = MUST LOGIN WITH PASSWORD TO GAIN THE WRITABLE PRIVILEGE
GUEST = CAN ACCESS AND VIEW THE FILE AND FOLDER, BUT NOT PRIVILEGE

---

### Post by swerdna on 2009-07-21
Make a directory called SHARED belonging to user ADMIN, group ADMIN, with permissions drwxr-xr-x, located at /path_to/SHARED

Make a directory called VIDEO belonging to user ADMIN, group ADMIN, with permissions drwxr-xr-x, located at /path_to/SHARED/VIDEO

Put these stanzas in smb.conf:
```
[SHARED]
path = /path_to/SHARED
read only = no
valid users = ADMIN

[VIDEO]
path = path_to/SHARED/VIDEO
read only = no
guest ok = yes
write list = ADMIN
```

For other ways to craft shares, see this tutorial: [Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by rawrico on 2009-07-22
thanks for replying
will try and see
after that will confirm with you about it....

---


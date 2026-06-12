---
title: "smbpasswd: Failed to find entry for user"
date: 2010-05-05
forum: General Help
---

### Post by linuxcss on 2010-05-05
I have create a desktop user as scanner2
using System->administration->user and groups

i try the following

/home/admin1# smbpasswd scanner2
New SMB password:
Retype new SMB password:
Failed to find entry for user scanner2.


what is wrong? need help 

I also can login as scanner2

no updates have been recently applied

---

### Post by lisati on 2010-05-05
You might want to try the following:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```
The first adds your choice of user name to samba and prompts you for a samba password. The second line enables the user name.

---

### Post by NagWolf on 2012-11-12
Hi All

Tried and tested, works the ticket. Thanx Lisati

---


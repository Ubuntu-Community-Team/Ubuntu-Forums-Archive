---
title: "Can't share my FAT 32 drive with smb?"
date: 2010-12-21
forum: General Help
---

### Post by hanez on 2010-12-21
Hi, Im trying to share a drive through smb without a password.

So far I changed security to share, guest account=nobody

and I made a new share:

[guest share]
comment = guest
path = /media/Big\ Drive/
browseable = yes
read only = yes
guest ok = yes


But it wont work.   I tested by changing the path to root (/)  and it works that way I can see almost everything in my comptuer ... I can see everything, but then when I go to media and click on BIG DRIVE, it still doesnt work.  I figure this is for one of the two reasons:

Its a Fat or NTFS drive and theres a problem with that
or
Theres a space in the directory 


Which is it, and how do I fix it please? :)

Also, how do I make this drive automount?  I notice it doesnt work until I click on it through the desktop.

---

### Post by hanez on 2010-12-29
extremely annoying... anyone know the answer?  I can share anything but my fat drive.

---

### Post by hanez on 2010-12-29
Found a solution, where the line in my smb.conf said guest account = nobody, I changed nobody to my default user.

---


---
title: "Windows Backup + Share"
date: 2012-04-19
forum: General Help
---

### Post by Kaaskilde on 2012-04-19
Hi all,

 I'm more or less new to using Ubuntu, but I have taking it to me and is trying to get it up and running.

 I got some problems that I do not quite understand how to use mask, for example "0777" to set rights, I can not quite see how to arrive at the figures I've been looking for a table or something that could help me but have not found one yet.

 But I have been asked to make some backup from a Windows 7 client onto an Ubuntu 11.10 server, I would use the "Windows Backup" option, but when I try to connect to my Ubuntu share from the "Windows Backup" it says requires "Full Rights" and then it here I come to a halt. 
I put rights via Samba like this: 
 [kaa]
 comment = kaa backup share
 path = /firm/Backup/Users/kaa
 guest ok = no
 browseable = yes
 writeable = yes
 valid users = kaa

 Is there anyone who can help here? (It should be the clients that pushes the backup on to the server)

 I also have another question, if we take the above code:
 [kaa]
 comment = kaa backup share
 path = /firm/Backup/Users/kaa
 guest ok = no
 browseable = yes
 writeable = yes
 valid users = kaa

 Here I point to "path = /firm/Backup/Users/kaa" then I would think it was there my rights were set, but then i set the rights on that level It goes all the way up to the top of the structure /firm. Is there a way for me to set rights/permissions on a single layer of a folder, if i want all to see the /firm/Backup/User/ but they should not enter the /kaa folder?


//Kaaskilde

---


---
title: "Need some filesharing help"
date: 2011-10-10
forum: General Help
---

### Post by qingpool on 2011-10-10
Hei

My knowledge is very basic on this subject so i need some help.

Using Ubuntu 11.04 and i have a folder "Backup" shared with other computers. A certain application creates it's backup files in that particular folder. Other computers can access it, but cannot copy files from it. 

Other computers connect using the same account credentials as i use on the Ubuntu machine. 

I have tried chowning the folder and chmodding 777, but it doesnt help - all new files created by the program give me no access rights.

How can i set it up so i dont have to chmod this folder every day?

For filesharing i use regular GUI filesharing.

Thanks

---

### Post by qingpool on 2011-10-12
I tried with a Samba share:

[backup]
comment = Backups
read only = no
path = /..../Backup
guest ok = no
browseable = yes
create mask = 0777

Still the files created in this directory cannot be edited (copied to) from a Windows machine when accessing over network.

Since i cannot umask a specific directory, i put umask 002 in this users .bashrc, this didnt also help.

I can edit these files after using:
sudo chmod -R 777 /Backup

but every new file created will still be read-only. All i need is to copy these files to a Windows machine - i have setup a program on Win 7  to check for new files in this directory and copy them if needed.

Help!

Regards

---


---
title: "Cannot open Windows Folder after backing up"
date: 2010-09-07
forum: General Help
---

### Post by mauro24 on 2010-09-07
I backed up a windows xp folder which was My documents to an ext4 formated external hard drive from an ubuntu 10.04 live cd.  After installing Ubuntu 10.04 on that same computer, I tried to open the my document folder then i was denied access to it because i was the wrong user.  In windows xp, the My documents folder was not password protected.  Is there any way to hack that folder, I have a bunch of pictures in there that I want to retrieve.  On the folder icon, it shows and x and a lock.  I think it means that is either encrypted or password protected.  I'm not sure so I'm asking for help.  Thanks in advanced.

---

### Post by davidmohammed on 2010-09-07
type in a terminal session

gksudo nautilus

this will give you a gui filemanager running as root - be careful!

---

### Post by Gone fishing on 2010-09-07
I would think you could just gksu nautilus and navigate to the folder you should be able to read no problem. You can also change the permissions of the folder with chown -R username /pathtodirectory

---


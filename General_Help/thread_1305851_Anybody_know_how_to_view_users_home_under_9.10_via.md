---
title: "Anybody know how to view users /home under 9.10 via samba"
date: 2009-10-30
forum: General Help
---

### Post by dj-toonz on 2009-10-30
Hi all, I've got samba set up to try to share my /home but having problems :( I can access the drive in windows XP pro on another machine that I've got but I don't see any of the folders or anything, I just see 4 files 3 show up invisible & 1 what says READ THIS, i think my drive is encrypted, Is there any way now I can share the Desktops Karmic Drive, or any way I can remove the encryption on the drive?

---

### Post by ghostborg on 2009-10-30
Did ya set the samba pw?
Just replace the all caps USERNAME with yours as the following link shows you.


[http://www.jonathanmoeller.com/screed/?p=1168]("http://www.jonathanmoeller.com/screed/?p=1168")

sudo smbpasswd -a USERNAME

---


---
title: "Have linux box pull files from windows through rsync"
date: 2012-08-13
forum: General Help
---

### Post by dannyvanderzande on 2012-08-13
Is it possible to have my linux server pull files from my girlfriends windows pc using rsync? Does anyone know a way?

I tried several apps but they all send it from windows to my linux server but I want the opposite to be in control when and how much backups are made.

---

### Post by lukeiamyourfather on 2012-08-13
Are you trying to backup files from the Windows machine to the Linux machine? If so I'd mount a share from the Linux machine on the Windows machine and use Robocopy (like rsync but from Microsoft). Or you could use rsync on the Windows machine through Cygwin.

If you must initiate the backup from the Linux machine you'd have to share everything you want to backup from the Windows machine and mount it on the Linux machine. Either way works I suppose.

---

### Post by dannyvanderzande on 2012-08-13
I am trying to backup up file that are on a windows machine by accessing it from a linux server using rsync. I have a nice full/incr backup script which works great for backing up my linux pc so I'd like to use it for the windows pc as well

---

### Post by asmoore82 on 2012-08-13
Cygwin is the only way I know of that might truly work. But even then there are no magic fixes for file ownership/permissions.

---

### Post by dannyvanderzande on 2012-08-14
Thanks a lot! It took me some time to get it installed but now I have it up and running it seems to do exactly what I want!

yay!

---


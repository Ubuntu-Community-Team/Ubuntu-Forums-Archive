---
title: "Getting things to run at startup"
date: 2011-06-05
forum: General Help
---

### Post by griffsterb on 2011-06-05
So I'm trying to get mediatomb to run at startup automatically. I went into System Settings -> Startup Applications and added a new one with the command 'sudo mediatomb.' Unsurprisingly it did not work. What am I doing wrong?

Also, what do I use in ubuntu to check for updates to all of my installed applications?

---

### Post by griffsterb on 2011-06-05
I found one problem. Not sure if I have more. My media files are all on a separate hard drive that I have to mount once I log in to ubuntu. Mediatomb says that the folders can't be found unless I mount the proper drive first, then it finds them. 

So on startup I guess I need to mount the drive first, then run mediatomb? how would i go about doing that?

---

### Post by griffsterb on 2011-06-05
bump

---

### Post by pqwoerituytrueiwoq on 2011-06-05
you can auto mount drives using fstab
 gksudo gedit /etc/fstab 
also read the manual
man fstab
edit it did not work because it needs a password in a tty
sudo fails if it is not run in a terminal
does the app really need root access?

---


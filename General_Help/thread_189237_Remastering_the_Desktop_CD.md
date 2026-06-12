---
title: "Remastering the Desktop CD"
date: 2006-06-05
forum: General Help
---

### Post by qalimas on 2006-06-05
Ok, so I've been able to remaster the Dapper Desktop CD and add in programs, but they don't appear in the menu.  I'd like to add files and such settings in the default home directory, but all of that is created on bootup.  If I could add files, then I could tweak the programs settings the way I wanted, instead of placing all my wanted files in a 0777 directory in /opt.

Any ideas on how to add and modify the default user home directory of the live Desktop CD?  Also, upon install, will all my changes be in the installed environment, including anything I added to /home/ubuntu (but copied over to the home directory of the user created during install)?

Thanks for any help you can give me :D

---

### Post by nalmeth on 2006-06-05
You would have to create a persistent /home folder on your harddrive (in which case you might as well just install anyway), or use a USB stick.

I do not think that any changes in the liveCD will be installed to the harddrive.

---

### Post by Rinzwind on 2006-06-05
Calimas: have a look at 'kickstart'.
It's in the repositories ;)

---

### Post by qalimas on 2006-06-05
Thanks for the help guys, but I found the directory after mounting the squashfs (/etc/skel).  I don't know about the installign yet, but I guess I'll find out soon :D

---


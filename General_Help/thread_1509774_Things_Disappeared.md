---
title: "Things Disappeared"
date: 2010-06-14
forum: General Help
---

### Post by MusicalAlchemy on 2010-06-14
I updated through the update manager the other day and after I shut my computer down and turned it back on the next day, all my icons on my desktop disappeared and I can't access my files or my applications.  It gives me this error when trying to access my files in my desktop. 

 Could not open location 'file:///home/anubis/Desktop'
No application is registered as handling this file.

I posted a new thread about this the other day and somehow the thread disappeared too.

So please help me, what do I need to do?

---

### Post by spiky001 on 2010-06-14
Have you got a wubi install of ubuntu or is it installed as only OS

---

### Post by MusicalAlchemy on 2010-06-14
I have Ubuntu installed as the only OS.

---

### Post by spiky001 on 2010-06-14
whats the output of 
```
df -l
```

---

### Post by MusicalAlchemy on 2010-06-14
anubis@Treedar:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            151263428   5792444 137787196   5% /
none                    441948       280    441668   1% /dev
none                    446452       140    446312   1% /dev/shm
none                    446452       180    446272   1% /var/run
none                    446452         0    446452   0% /var/lock
none                    446452         0    446452   0% /lib/init/rw
/dev/sdb1            244196000 197764460  46431540  81% /media/FreeAgent Drive

---

### Post by spiky001 on 2010-06-16
you have not got home mounted needs to be mounted

---


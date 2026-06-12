---
title: "Folder Sync."
date: 2009-06-27
forum: General Help
---

### Post by chaosdesigner on 2009-06-27
Ok so i had this idea that would make my life a lot easier, and i really dont know if its possibly, or how.

So first I will explain my thought. I have a internal Data Folder and a external Data Folder. I use that external Folder to backup my data, but when i add somethig new, i add it to the internal folder and i always need to added it to both folders.

So For example if i get a new song, and i add it to my normal, internal, musik folder. I want this music file to be automaticly added to the folder on my external hdd. The same the other way around. So as soon as I connect the external hdd those folders should 'merge'.

The question would be if tahts even possible.

Is it?

---

### Post by philcamlin on 2009-06-27
sorrry for this post above hes spamming the boards...

yes you can merge folders but you will have to do it manually there is no option for auto merge. not to my knowledge. 

i wish there was though :popcorn:

---

### Post by chaosdesigner on 2009-06-27
@philcamlin:

Thank you for you answer. I have foudn a programm called Unison, im testing it right now but it seems like there is not autosync here either. Maybe someone else knows a tool, would be really useful.

---

### Post by DGortze380 on 2009-06-27
rsync in a cron script would work well. You'll have to do some checking to make sure the drives are mounted.

---

### Post by corny on 2009-06-28
here is your autosync:
you can invoke unison on log in and log out gdm in /etc/gdm/PostLogin/Default and /etc/gdm/PostSession/default. just add

```
#!/bin/bash

# check if server is alive
# 1 (online), 0 (offline) 
Backupserver="MyServerName"
ServerHere=`ping -c1 $Backupserver | grep packet | awk '{print $4}'` 
if [ $ServerHere -eq 1 ]; then
  xterm -e su $USER -c "unison myprofile -batch=true -log=false"
fi
```
of course a cron job could do syncs also during your work additionally.

---

### Post by chaosdesigner on 2009-06-28
okay i have a little problem with unison. i want a local folder and a shared folder in the network to be synced, but unsion somehow cant handel with samba. 


it says.


```
ssh: connect to host 192.168.2.113 port 22: Connection refused
```

---


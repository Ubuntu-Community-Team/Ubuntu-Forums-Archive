---
title: "root folder access"
date: 2011-09-25
forum: General Help
---

### Post by crutch145 on 2011-09-25
I am receiving errors after running a backup using luckybackup and it says that to view the error logs, I have to go to /root/.luckyBackup/logs/.  How can I access those logs if the root folder has a big X on it and says I do not have permission to access that directory? 

Thanks, 

Justin

---

### Post by TeoBigusGeekus on 2011-09-25
Try with 
```
gksu nautilus /root/.luckyBackup/logs/
```

---

### Post by haqking on 2011-09-25
> **crutch145 said:**
> I am receiving errors after running a backup using luckybackup and it says that to view the error logs, I have to go to /root/.luckyBackup/logs/.  How can I access those logs if the root folder has a big X on it and says I do not have permission to access that directory? 

Thanks, 

Justin

read [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo")

root is locked by default in Ubuntu and we elevate priveleges using sudo or gksudo..

Peace

---

### Post by hal8000 on 2011-09-25
You either use sudo or copy the logs to your home folder to view them.


mkdir ~/logs
sudo cp -r /root/.luckyBackup/logs/* ~/logs/

Is one way to view the logs.

---

### Post by haqking on 2011-09-25
or use the gui log file viewer

```
gnome-system-log &
```

to view as root

```
gksudo gnome-system-log &
```

---

### Post by crutch145 on 2011-09-25
Thanks, [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094").  Your suggestion worked perfectly! 

Justin

---


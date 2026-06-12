---
title: "How to remove complete a package ?"
date: 2010-09-18
forum: General Help
---

### Post by kema_u on 2010-09-18
Hi! After i remove many applications from my system, i see that there are many temp files on my filesystem (not just from /home directory but also i see many temp files other directories.). So i am asking you how to remove a software completely from Ubuntu ?

Thank you!

---

### Post by kema_u on 2010-09-19
any help ? :(

---

### Post by SolvedSnake on 2010-09-19
Well, I'm pretty new to Ubuntu too, but I think the way to completely remove something is:

- Open Synaptic Package Manager
- Find the package you want to remove (quick search helps)
- Right click it, and click on mark for complete removal
- Click Apply in the toolbar

---

### Post by scorchgeek on 2010-09-19
```
sudo apt-get purge {package}
```
will delete the package as well as config files.

---

### Post by kema_u on 2010-09-20
[SolvedSnake]("http://ubuntuforums.org/member.php?u=1149356") [scorchgeek]("http://ubuntuforums.org/member.php?u=664866") i remove many times applications with your suggestions but they remove installation packages and /home directory s config files. But there are many other temp files. If you want check it yourself. For example: Install wine and install 3-4 applications for windows. after remove the package of wine (also use bleachib as root). End of everthing search files about wine or applications you had installed inside wine. and see the temp files which i want to tell you.

---

### Post by gandaran on 2010-09-20
> **kema_u said:**
> [SolvedSnake]("http://ubuntuforums.org/member.php?u=1149356") [scorchgeek]("http://ubuntuforums.org/member.php?u=664866") i remove many times applications with your suggestions but they remove installation packages and /home directory s config files. But there are many other temp files. If you want check it yourself. For example: Install wine and install 3-4 applications for windows. after remove the package of wine (also use bleachib as root). End of everthing search files about wine or applications you had installed inside wine. and see the temp files which i want to tell you.
complete removal of applications still won't remove the user configuration files, you have to do it yourself, to remove the wine c drive after uninstalling completely the wine program you have to delete the .wine folder in the hidden home user directory.
and temp files could still show up for a while in the database after removing the program, run the database update command if needed.
```
sudo updatedb
```

---


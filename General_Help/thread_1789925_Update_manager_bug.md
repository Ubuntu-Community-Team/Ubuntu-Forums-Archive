---
title: "Update manager bug"
date: 2011-06-24
forum: General Help
---

### Post by dnr1128 on 2011-06-24
This morning when i opened up my system I found that the update manager had tried to initialize and and was showing a bug.  AFter reboot, it happened again.  This is the error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any thoughts on what I can do?

11.04 on Lenovo IdeaPad Z565

---

### Post by LordNeo on 2011-06-24
Refresh and/or switch over the "Global Server" (in Software Sources)

---

### Post by Rubi1200 on 2011-06-24
And if switching to the Main Server doesn't work you can try these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by jerrrys on 2011-06-24
this seems to be going around

[http://ubuntuforums.org/showthread.php?p=10968594#post10968594](http://ubuntuforums.org/showthread.php?p=10968594#post10968594)

---

### Post by dnr1128 on 2011-06-24
That seems to have fixed the problem.  Thanks!

---

### Post by Rubi1200 on 2011-06-24
Excellent! Glad you got things sorted out :-)

---


---
title: "view logs"
date: 2010-09-08
forum: General Help
---

### Post by Sapper41 on 2010-09-08
Im having a random shot down problem, so i want to view my logs but Im having trouble doing that. In ubuntu 10.04 i go to System > Admin > then there is no system log tab like some guides have indicated. I have also tried navigating there via terminal but it says the directory doesnt exist. I imagine it is operator error. Some help would be great

---

### Post by andrewthomas on 2010-09-08
```
sudo apt-get install gnome-system-log
```

if you just want to look at the files, then 
```
gksudo nautilus
```then navigate to the /var/log folder

---


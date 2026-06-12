---
title: "How can I disable the window reflection on the desktop cube? [Ubuntu 9.10]"
date: 2010-01-17
forum: General Help
---

### Post by MiiPianist on 2010-01-17
Can anyone tell me if and how I can disable the window reflection on the desktop cube? I would appreciate it a lot if someone would...I'm trying to disable it but i cant find how...I tried disabling the reflection from the wallpaper but it got disabled by most of the windows then... PLEASE REPLY

---

### Post by fooman on 2010-01-17
is CCSM installed?  if not,  then open a terminal and type or copy/paste the following:

```
sudo apt-get install compizconfig-settings-manager
```

then open it in system > preferences > compizconfig settings manager

not sure what setting you are refering to,  but take a look under "effects" and uncheck "reflection"...if that does not do it,  then again look under effects > cube reflection and deformation > reflection tab,  and uncheck "enable".

hope that helps.

---

### Post by MiiPianist on 2010-01-17
Yes, I have CCSM installed. The reflection I'm talking about isn't the one in "Cube reflection and Deformation", its the one in "Reflection" i.e. the reflection for the window background. I have searched continously, but I didn't find any option entitled "Disable window reflection from Deasktop Cube", nor anything similar... If you are able to provide any further help about my problem, let me know.

---


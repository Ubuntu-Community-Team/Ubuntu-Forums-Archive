---
title: "New to Ubuntu! How to update?"
date: 2010-11-29
forum: General Help
---

### Post by zainlodhi on 2010-11-29
Hello! I just installed Ubuntu on my laptop. I am a keen user. I want to know how to update the system and/or install new software...

---

### Post by WorMzy on 2010-11-29
The update manager is under System -> Administration -> Update Manager

Or you can open a terminal and run
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by karthick87 on 2010-11-29
To install:
```
sudo apt-get install [COLOR=Red]packaganame[/COLOR]
```To uninstall:
```
sudo apt-get remove [COLOR=Red]packaganame[/COLOR]
```To uninstall packages and remove its configuration:
```
sudo apt-get --purge remove [COLOR=Red]packagename[/COLOR] 
```To update:
```
sudo apt-get update
sudo apt-get upgrade
```To clean caches:
```
sudo apt-get clean all
```

---

### Post by wojox on 2010-11-29
[SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")

---


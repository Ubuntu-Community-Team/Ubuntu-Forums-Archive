---
title: "how to install .rpm files in ubuntu"
date: 2006-05-27
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-27
heh i wanna install limewire and its is a .pm file i cant extrct it coz it says file type not supported i have only had dealing with .deb and .sh files can ne shed some light on ho to install .rpm files?

---

### Post by aysiu on 2006-05-27
Paste these commands into a terminal: ```
sudo aptitude update
sudo aptitude install alien
ls
cd ~/Desktop
ls
sudo alien -i lime*.rpm
```

---

### Post by mjziegle on 2006-05-27
Use gtk-gnutella

sudo apt-get install gtk-gnutella

It is a limewire (gnutella) network compatible client.

---

### Post by nismoskys on 2006-05-27
since u just want limewire you could just
```
sudo apt-get install frostwire
``` (opensource limewire)

---

### Post by LORD_PoLvO on 2006-05-27
thnx guys but i allready have limwire intsalled from the first post lol but thnx neway

---


---
title: "how to install openoffice in 10.4?"
date: 2010-08-31
forum: General Help
---

### Post by enhu on 2010-08-31
it seems like it didn't found openoffice in the repo.

---

### Post by bergfly on 2010-08-31
It is definitely in there. What package manager tool are you using?

---

### Post by enhu on 2010-08-31
synaptic manager seems not working too . :D

root@ubuntu:/home/enhu/Downloads# apt-get install openoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
root@ubuntu:/home/enhu/Downloads#

---

### Post by jerome1232 on 2010-08-31
openoffice.org would be the package name.

pretty sure parts of open office should be installed by default though.

---

### Post by enhu on 2010-08-31
thanks jerome. 
lolz.. ubuntu is funny.. why would they have to put .org on it. :P

---

### Post by wojox on 2010-08-31
> **enhu said:**
> thanks jerome. 
lolz.. ubuntu is funny.. why would they have to put .org on it. :P

Linux is very precise like that. :P

---

### Post by jerome1232 on 2010-08-31
Probably because the actual name of the project is OpenOffice.org, in your menu's and on it's splash screens you'll see OpenOffice.org, that's the name.

You can always do a search in synaptic or use apt-cache to figure out exact names of packages if you are not sure.

ie

```
apt-cache search open office
```

---


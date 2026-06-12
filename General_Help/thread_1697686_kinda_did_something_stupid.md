---
title: "kinda did something stupid"
date: 2011-03-01
forum: General Help
---

### Post by jason.b.c on 2011-03-01
long story  so i'm not gonna go into it much..

i removed network manager not thinking clearly..

wound up with no internet , i have NM back now but it complained that the network management wasn't running , so with a forum search i found :



```
sudo service network-manager start
```

and that brought the connection back on ...


my question is , how do i make sure i don't have to enter that command on every restart??  in other words , will the networking autostart like normal from now on ?

---

### Post by TeoBigusGeekus on 2011-03-01
Isn't there something about network manager in Administration>Preferences>Startup apps?

---

### Post by jason.b.c on 2011-03-01
> **TeoBigusGeekus said:**
> Isn't there something about network manager in Administration>Preferences>Startup apps?

well yes , i have that enabled (again) , but i'm just trying to figure out why nm-applet keeps crashing..  

just did a restart and nm didn't autostart , the check box in startup Is checked...

---


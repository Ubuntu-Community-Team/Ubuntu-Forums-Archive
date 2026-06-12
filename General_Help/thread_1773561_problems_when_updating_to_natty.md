---
title: "problems when updating to natty"
date: 2011-06-02
forum: General Help
---

### Post by sprinkl3m0nstur on 2011-06-02
alright i decided i would upgrade to natty on my netbook and i updated using the update manager everything went fine until it came to restarting once i had restarted and logged in my netbook (an asus eeepc 1001 which was running ubuntu 10.10) it locks up just after log in and and i cant do anything, what do i do?

---

### Post by wgarcia on 2011-06-02
Did you have Ubuntu Netbook Remix before updating? In that case I've seen that in the login screen the option to log is still Ubuntu Netbook Remix which locks it after entering the password because this desktop is uninstalled with the update. 

If this is the case you just have to change the desktop to "Ubuntu" after entering your user name and before entering the password (at the lower bar you have the place to choose your desktop).

---

### Post by sprinkl3m0nstur on 2011-06-02
ok i found the only way i can get to the desktop is by entering in safe mode, how should i go about finishing the update seeing as the updating process didnt automatically resume

---

### Post by iclestu on 2011-06-02
> **sprinkl3m0nstur said:**
> ok i found the only way i can get to the desktop is by entering in safe mode, how should i go about finishing the update seeing as the updating process didnt automatically resume


```
sudo dpkg --configure -a
```

---


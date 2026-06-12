---
title: "VIdeo Card Settings"
date: 2009-12-20
forum: General Help
---

### Post by aantaya on 2009-12-20
Hi all, just getting into the Ubuntu, but I am having an issue with my graphics card settings, and ubuntu remembering them. I am using the latest driver, but every time I restart my machine I still get 1 monitor detected and I have to go back in to the settings and enable the 2nd monitor. 

I am using a Nvidia card Geoforce 4, about a 3 year old card. one thing I get is I try to "save to X configureation File" thinking that might help but I get a "failure to Parse existing x confif file '/ect/x11/xorg.conf' " Error.

---

### Post by Dark_Stang on 2009-12-20
Two things.
1. Try renaming the current /etc/X11/xorg.conf file to something like /etc/X11/xorg.conf.backup
2. Make sure you're running the nvidia settings manager with root permission or you'll just get another error.

---

### Post by aantaya on 2009-12-20
I can no rename this file and if I try to delete it I get a Permission denied.

---

### Post by Treeh on 2009-12-20
> **aantaya said:**
> I can no rename this file and if I try to delete it I get a Permission denied.

If you're doing it through the GUI, open the file manager (Nautilus) and run the following using Alt + F2:

```
gksudo nautilus
```and using terminal:

```
 sudo rm yourfile 
```You couldn't delete it because you didn't have root privileges, both of these methods grant them.

But...I recommended saving it as a back-up:

```

cd /etc/X11/
sudo cp xorg.conf xorg.conf.backup
sudo rm xorg.conf

```

---

### Post by aantaya on 2009-12-20
Awesome, thank you both very much!

---


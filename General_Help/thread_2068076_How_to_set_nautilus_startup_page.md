---
title: "How to set nautilus startup page"
date: 2012-10-08
forum: General Help
---

### Post by zcnnbb on 2012-10-08
by default, nautilus will open $HOME will started.
Today, I want to use a customized location as its startup page

---

### Post by cipherboy_loc on 2012-10-08
You could create a custom .desktop file and specify a path on the exec line. Clicking that launcher would take you to that directory rather than your home one.


Thanks,
Cipherboy

---

### Post by HiImTye on 2012-10-08
if you want it on your desktop, 'make link here' and then drag it to the desktop
if you want to change the folder for 'Files' then go to 'main menu' and then change the 'command' line from
```
nautilus %U
```
to
```
nautilus *folderpath*
```

---

### Post by zcnnbb on 2012-10-08
> **cipherboy_loc said:**
> You could create a custom .desktop file and specify a path on the exec line. Clicking that launcher would take you to that directory rather than your home one.


Thanks,
Cipherboy


This is not what I want.
I want to know if there is a setting (GUI settings or dconf settings) which can implement it.

---

### Post by HiImTye on 2012-10-09
nautilus defaults to your home folder. if you want to open a different folder, just feed it a folder path, as I already explained

---


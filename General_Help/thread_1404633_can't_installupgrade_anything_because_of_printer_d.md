---
title: "can't install/upgrade anything because of printer driver"
date: 2010-02-11
forum: General Help
---

### Post by sosky on 2010-02-11
hi
I installed printer drivers from a deb package and now I can't install/update anything!! I get this error: 

jordan@jordan-desktop:~$ sudo apt-get install gtk-recordmydesktop
[sudo] password for jordan: 
Sorry, try again.
[sudo] password for jordan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gtk-recordmydesktop: Depends: recordmydesktop (>= 0.3.8) but it is not going to be installed
  pstocanonbj: Depends: libcupsys2 (>= 1.2.3)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Why is this 1 error tying up the entire install system?

thanks

---

### Post by jken146 on 2010-02-11
Do what it suggests.
```
sudo apt-get -f install
```

---

### Post by sosky on 2010-02-11
Hi,

It suggest that I remove the package that I installed to get my printer to work.

---

### Post by jken146 on 2010-02-12
Is libcupsys2 installed?

---

### Post by sosky on 2010-02-12
thank you so much!!!

---


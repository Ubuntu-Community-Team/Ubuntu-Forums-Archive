---
title: "Missing FILES HELP!!!"
date: 2006-01-29
forum: General Help
---

### Post by Bubs on 2006-01-29
I installed ubuntu then wanted to see what the kde desktop looked like so I then installed it and I think it uninstalled some of the gnome peices of the desktop.

like when I start firefox i get a local file of ubuntu help, and now I don't get it.

so short of reinstalling ubuntu How do I get all the original pakages back and remove all of the kubuntu.

cause I really don't want to reinstall

---

### Post by darth_vector on 2006-01-29
to remove kde```
sudo apt-get remove --purge kde
```and to reinstall gnome```
sudo apt-get install --reinstall gdm
```

---

### Post by Bubs on 2006-01-30
thanks that help out a lot

---

### Post by Bubs on 2006-01-30
It doens't 

      i can still log into kde and it the terminal it gives me this
```
 bubs@ubuntu-bubs:~$ sudo apt-get remove --purge kde
Reading package lists... Done
Building dependency tree... Done
Package kde is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bubs@ubuntu-bubs:~$

```

---

### Post by kaamos on 2006-01-30
You can get the original gnome packages back with
```
sudo apt-get install ubuntu-desktop
```
Removing kde depends on the way you installed it.

---

### Post by Bubs on 2006-01-31
I installed it through the terminal

I think it was:                 sudo apt-get install kubuntu-desktop

found it at this site [http://easylinux.info/wiki/Ubuntu#How_to_install_KDE](http://easylinux.info/wiki/Ubuntu#How_to_install_KDE)

---


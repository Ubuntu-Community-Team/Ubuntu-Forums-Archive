---
title: "Server Install"
date: 2006-05-26
forum: General Help
---

### Post by thunderduck3141 on 2006-05-26
hi all
does anybody know the packages i need to install (i have the server option installed) in order to get x and gnome running
thanks

---

### Post by barbarian on 2006-05-26
Hi,
I gess You need *ubuntu-desktop*:-)

---

### Post by Sutekh on 2006-05-26
To get the default Ubuntu/GNOME desktop you should install the ubuntu-desktop package (as suggested).  You should use these commands straight after the server install
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by thunderduck3141 on 2006-05-26
thing is i dont want all that extra stuff (like the egia sodtphone and stuff) just gnome running

---

### Post by Sutekh on 2006-05-26
If you just want GNOME not Ubuntu, then you might consider the gnome-desktop-environment package.

[Ubuntu Packages - gnome-desktop-environmentp](http://packages.ubuntu.com/breezy/gnome/gnome-desktop-environment)

You will need the [universe repository enabled](http://psychocats.net/ubuntu/sources.php), and then install using
```
sudo apt-get update
sudo apt-get install gnome-desktop-environment
```

---


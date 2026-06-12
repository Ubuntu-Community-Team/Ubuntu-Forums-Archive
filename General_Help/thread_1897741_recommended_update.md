---
title: "recommended update"
date: 2011-12-19
forum: General Help
---

### Post by ernestj on 2011-12-19
I turned on my computer and it showed that I had some system updates that needed to be downloaded. I clicked to show the packages for download and was dumb-founded to find that most of the  packages were for KDE. I am have Xubuntu with XFCE. 

What is up with all of the KDE stuff? Is this stuff gonna slow me down or won't effect me if I do not use KDE on my system?

Thanks,
Ernie

---

### Post by hhh on 2011-12-19
Maybe you have a Qt application or two (maybe Amarok?) that pulls in some KDE packages? Type this in a terminal and post what packages it wants to install here (type "n" without quotes or just close the terminal to prevent the actual update)...
```
sudo apt-get dist-upgrade
```

---

### Post by ernestj on 2011-12-19
I have Clementine. Could that be it?

Thanks,
Ernie

---

### Post by MartijnNL on 2011-12-20
It could. "It is a port of Amarok 1.4 to the Qt 4 framework and the GStreamer multimedia framework." As it uses Qt if probably has KDE software as dependencies.

If you don't want KDE software, you'll need to use a different music player. (And after uninstalling clementine autoremove the rest of the packages.)

---

### Post by mike555 on 2011-12-20
I have clementine , and it did NOT install any kde stuff on my Xubuntu install ........


 of course I have "treat recommends as required " turned off on the package manager and the software center ... as I suggest you do , so you will not get a bunch of extra stuff installed that is not needed ...

---


---
title: "installing KDE"
date: 2011-04-21
forum: General Help
---

### Post by ki4jgt on 2011-04-21
How do you install KDE without adding all the extra applications which come with it? I have gnome already installed and would simply like to install kde envirnment and not the terminal client the browser or any of it's other software.

---

### Post by kn0w-b1nary on 2011-04-21
just run:

```
sudo apt-get install kdebase-workspace-bin
```

---

### Post by ki4jgt on 2011-04-23
Thanks

---

### Post by ki4jgt on 2011-04-23
```
jesse@Ubuntu-Machine:~$ sudo aptitude install kdebase-workspace-bin
[sudo] password for jesse: 
The following NEW packages will be installed:
  kdebase-runtime{a} kdebase-workspace-bin kubuntu-debug-installer{a} 
  libkdewebkit5{a} libkworkspace4{a} libplasma3{a} 
  libplasmagenericshell4{a} libpowerdevilcore0{a} libprocessui4a{a} 
  libqtwebkit4{a} phonon{a} phonon-backend-gstreamer{a} 
  plasma-scriptengine-declarative{a} plasma-scriptengine-javascript{a} 
  polkit-kde-1{a} qapt-batch{a} 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.8 kB/10.5 MB of archives. After unpacking 47.3 MB will be used.
Do you want to continue? [Y/n/?] y
Err http://us.archive.ubuntu.com/ubuntu/ natty/main phonon-backend-gstreamer i386 4:4.7.0really4.4.4-0ubuntu3
  404  Not Found [IP: 91.189.92.170 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/phonon-backend-gstreamer/phonon-backend-gstreamer_4.7.0really4.4.4-0ubuntu3_i386.deb: 404  Not Found [IP: 91.189.92.170 80]

```

I also can't choose this UI on the login screen?

---

### Post by ki4jgt on 2011-04-23
Rebooted and it installed great. Now every time I choose the KDE theme, it only shows a black screen when I sign in. It gives a notice that my battery has gone bad and then the screen remains black.

---


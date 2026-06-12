---
title: "Software Index is Broken"
date: 2012-06-18
forum: General Help
---

### Post by Shodai24 on 2012-06-18
Greetings. I recently had a problem when trying to install a package called gnome-themes-extras. it did not work out properly and now whenever I want to install something it says that the index/catalog is broken. I tried to correct this using apt-get -f install and it returned the following.


[SIZE="1"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  icedax
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-themes-extras
The following NEW packages will be installed:
  gnome-themes-extras
0 upgraded, 1 newly installed, 0 to remove and 426 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,585 kB of archives.
After this operation, 13.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 332492 files and directories currently installed.)
Unpacking gnome-themes-extras (from .../gnome-themes-extras_2.22.0-3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/Unity/index.theme', which is also in package unity-theme 1.0ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE]
I do not know how to proceed and I urgently need to upgrade to 11.10 then 12.04 but it will not allow me to due to the broken index. Please help!

---

### Post by cortman on 2012-06-18
> **Shodai24 said:**
> Greetings. I recently had a problem when trying to install a package called gnome-themes-extras. it did not work out properly and now whenever I want to install something it says that the index/catalog is broken. I tried to correct this using apt-get -f install and it returned the following.


[SIZE="1"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  icedax
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-themes-extras
The following NEW packages will be installed:
  gnome-themes-extras
0 upgraded, 1 newly installed, 0 to remove and 426 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,585 kB of archives.
After this operation, 13.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 332492 files and directories currently installed.)
Unpacking gnome-themes-extras (from .../gnome-themes-extras_2.22.0-3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/Unity/index.theme', which is also in package unity-theme 1.0ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/SIZE]
I do not know how to proceed and I urgently need to upgrade to 11.10 then 12.04 but it will not allow me to due to the broken index. Please help!

Hi, run

```
sudo rm /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install gnome-themes-extras
```

---

### Post by Shodai24 on 2012-06-18
It is still not working. I even ran apt-get -f install and it came up with this error.


Unpacking gnome-themes-extras (from .../gnome-themes-extras_2.22.0-3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb (--unpack):
 trying to overwrite '/usr/share/themes/Unity/index.theme', which is also in package unity-theme 1.0ubuntu4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-themes-extras_2.22.0-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Will reinstalling the system or installing a new version from a LiveCD solve the problem?

---

### Post by jmfal on 2012-06-18
Try
```
 sudo dpkg  --configure  -a 
```

then redo commands from Cortman

---


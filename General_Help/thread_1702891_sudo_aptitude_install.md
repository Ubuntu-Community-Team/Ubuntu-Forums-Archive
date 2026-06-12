---
title: "sudo aptitude install"
date: 2011-03-08
forum: General Help
---

### Post by Enigmapond on 2011-03-08
Hi!

I just have a question regarding this command. Below is the list that follows.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  choqok vlc-110 
The following NEW packages will be installed:
  bzr bzrtools claws-mail claws-mail-i18n gnome-screensaver libcompfaceg1 libdirac-decoder0 
  libetpan13 libggi-target-x libggi2 libggiwmh0 libggiwmh0-target-x libgii1 libgii1-target-x 
  libgoom2 libmysqlclient16 libopenraw1 libopenrawgnome1 libosso1 libprojectm2 
  libqt4-sql-mysql libreoffice-filter-binfilter libva-x11-1 libwpd8c2a libwpg-0.1-1 
  libwps-0.1-1 libxcb-randr0 libxcb-render-util0 libzvbi-common libzvbi0 
  linux-headers-2.6.32-24 linux-headers-2.6.32-24-lowlatency linux-headers-2.6.32-27 
  linux-headers-2.6.32-27-generic linux-headers-2.6.32-28 linux-headers-2.6.32-28-generic 
  linux-headers-lowlatency linux-image-2.6.32-24-lowlatency linux-image-2.6.32-27-generic 
  linux-image-2.6.32-28-generic linux-image-lowlatency linux-lowlatency 
  mysql-client-core-5.1 mysql-common mysql-server-core-5.1 openoffice.org-l10n-common 
  projectm-data python-paramiko screenlets wx2.8-i18n 
The following packages are RECOMMENDED but will NOT be installed:
  python-evolution python-gnome2-desktop python-gtkmozembed 
0 packages upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 176MB of archives. After unpacking 797MB will be used.
The following packages have unmet dependencies:
  vlc-110: Depends: libdvbpsi5 but it is not installable
           Depends: libupnp3 (>= 1.4.3) but it is not installable
           Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
  choqok: Depends: libqjson0 but it is not installable
          Depends: libqoauth1 but it is not installable
          Depends: libqca2-plugin-ossl but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
python-evolution [2.30.0-0ubuntu1 (lucid)]
python-gtkmozembed [2.25.3-4.1ubuntu4 (lucid)]

Keep the following packages at their current version:
choqok [Not Installed]
vlc-110 [Not Installed]

Score is 170

Accept this solution? [Y/n/q/?
```

My question is should all these things be installed? Even the previous kernels?

Thank you!

---

### Post by simonmoon42 on 2011-03-08
The short answer is yes. The software you're trying to install is dependent on those packages.

---

### Post by Enigmapond on 2011-03-08
Thanks for the reply but that seems a bit odd as I'm not trying to install anything...I just ran that command without a package name.

---

### Post by simonmoon42 on 2011-03-08
I believe if you leave it blank it will upgrade all installed packages.

---

### Post by vivek.pandey on 2011-03-08
here is what i get


vivek@NEO:~$ sudo apt-get install
[sudo] password for vivek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
vivek@NEO:~$

---

### Post by Enigmapond on 2011-03-08
> **neo_aryan said:**
> here is what i get


vivek@NEO:~$ sudo apt-get install
[sudo] password for vivek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
vivek@NEO:~$

I didn't use apt-get.....I used "aptitude"

All my install programmes are updated daily and there are none out there right now. This is a partial list of things I had, at one time, like the previous linux images and openoffice, I now use LibreOffice and there is nothing OpenOffice left on my system. I even purged the config files for the images so there is also nothing of them left.

---

### Post by vivek.pandey on 2011-03-08
are you sure you used sudo aptitude install?
i am gettin command not found error
vivek@NEO:~$ sudo aptitude install
[sudo] password for vivek: 
sudo: aptitude: command not found
vivek@NEO:~$

---

### Post by Enigmapond on 2011-03-08
> **neo_aryan said:**
> are you sure you used sudo aptitude install?
i am gettin command not found error
vivek@NEO:~$ sudo aptitude install
[sudo] password for vivek: 
sudo: aptitude: command not found
vivek@NEO:~$
Thank you but...I'm quiet sure. I always use aptitude.

---

### Post by plucky on 2011-03-08
> are you sure you used sudo aptitude install?

The OP is running Lucid 10.04 which has aptitude installed by default.

If you are running Maverick 10.10,aptitude was not installed by default.

> 
The following packages are BROKEN:
  choqok vlc-110 


Try ```
sudo aptitude update
sudo aptitude install -f
```

Good Luck

---


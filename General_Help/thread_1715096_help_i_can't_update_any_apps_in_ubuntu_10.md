---
title: "help i can't update any apps in ubuntu 10"
date: 2011-03-26
forum: General Help
---

### Post by MrStranger on 2011-03-26
hey . when i try to update any apps or updagrade 'em it doen't work for exmple if i wan to upgrade my firefox tp the new version look what i have : 

> sudo apt-get upgrade firefox 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nmap python-pexpect
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

thx for help

---

### Post by Frogs Hair on 2011-03-26
Firefox 4 stable```
sudo add-apt-repository ppa:mozillateam/firefox-stable
``````
sudo apt-get update
``````
sudo apt-get install firefox
```

---

### Post by MrStranger on 2011-03-26
thx man it's work but about the other apps ......... do i need make the somethings

---

### Post by Frogs Hair on 2011-03-26
What applications ? When you install applications via the software center you will receive updates specific to the software for the Ubuntu release you are using . You most likely had FF 3.6.XX included with your current release and that is why FF did not update to FF4 automatically .

Are you having problems with the update manager  ? If you install the latest version of a program from a website  they will not be updated via the update manager , It is recommended to use programs from the repository because they are best suited to your current release. You will most likely see a newer version in the next Ubuntu release.

---

### Post by MrStranger on 2011-03-26
my problem is if i wan to update to upgrade new version of any apps it shows me the some thing as when i update firefox for exmple to upgrade thundebrid i had : 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird is already the newest version.
The following packages were automatically installed and are no longer required:
  ttf-wqy-zenhei ttf-kochi-mincho ttf-kannada-fonts linux-headers-2.6.35-22
  libaccess-bridge-java ttf-kochi-gothic linux-headers-2.6.35-22-generic
  libgif4 ttf-telugu-fonts ttf-oriya-fonts ttf-bengali-fonts
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
 
and the some thing for all apps that i wan to update or to install .;; thnx

---

### Post by MrEgg on 2011-03-26
The correct syntax is

```
sudo apt-get upgrade
```

and NOT
```
sudo apt-get upgrade firefox
```

apt-get upgrades everything, you can't select. If you want to select which packages to upgrade, then you have to use either Synaptic or the Update Manager, both from the System - Administration menu.

---


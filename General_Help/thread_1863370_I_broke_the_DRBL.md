---
title: "I broke the DRBL"
date: 2011-10-17
forum: General Help
---

### Post by Mr.Enigma on 2011-10-17
okay i'm following this guide: [https://wiki.edubuntu.org/SettingUpClonezillaDRBLonUbuntu](https://wiki.edubuntu.org/SettingUpClonezillaDRBLonUbuntu)

And ater running the below command a couple of times trying to play with it I think i've broken it.
```
sudo /opt/drbl/sbin/drblpush -i
```

I want to use eth0 to connect to a switch that's not on our main network, and use wlan0 to use Internet. 
However, it keeps using eth0 as the internet and using wlan0 as the DRBL environment, and i'm clueless of how to change it.

I should point out that I'm completely new to Linux.
And I'm trying to use clonezilla to deploy Windows 7 images using PXE

I tried 
```
sudo apt-get remove drbl
sudo apt-get install drbl
```
to try to refresh the config file but that didn't seem to do it because it came back with 

```
 sudo apt-get install drbl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  drbl
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 0 B/2,239 kB of archives.
After this operation, 14.8 MB of additional disk space will be used.
Selecting previously deselected package drbl.
(Reading database ... 148932 files and directories currently installed.)
Unpacking drbl (from .../drbl_1.10.31-1drbl_all.deb) ...
Setting up drbl (1.10.31-1drbl) ...
```


Any help you guys can give will be amazing.

---


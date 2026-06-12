---
title: "Ubuntu on WinXP's  LAN"
date: 2005-02-28
forum: General Help
---

### Post by dejavu on 2005-02-28
heres the Situation
=============

i got my system connected to a LAN of 3 more PCs .. all running on WinXP !  I used WinXP before but now ive switched to Linux(ubuntu) with winXP still installed in another HDD on the same system (dual boot) ...  once i got the card and all the stuff configured i was  able to PING and Transfer data among all the systems of the network ..  but there is still a big Problem !!

Problem 
=====

All the Data and the Goodies i have downloaded and used and present in the Windows HDD which are mounted on my linux OS but they are not Accessible to other users of the LAN... 

in simple words all the data that i have on my winDrives ...that is VFAT and NTFS can be accessed by me on the linux system by just mounting them ... but i want others on the network to Access those Drives as well with me using Ubuntu and not restarting and running XP again !!  

Request
=-====

How can i Configure my Ubuntu system to show my window drives to All the other ppl on LAN who are all using WinXP . Do i need to conf SAMBA for it .. what other software do i need.... 


(we all are connected to eachother from a Switch and all the systems are on WinXP .. only im on Ubuntu)

---

### Post by nemin on 2005-02-28
[QUOTE=dejavu]
How can i Configure my Ubuntu system to show my window drives to All the other ppl on LAN who are all using WinXP . Do i need to conf SAMBA for it .. what other software do i need.... 
[/QUOTE]
Samba is the only thing you need for this, you'll probably find [http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba) usefull.

---


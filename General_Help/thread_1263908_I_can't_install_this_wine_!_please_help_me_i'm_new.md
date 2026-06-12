---
title: "I can't install this wine ! please help me i'm newbie"
date: 2009-09-11
forum: General Help
---

### Post by puya4ever on 2009-09-11
Hi . I'm new at ubuntu , it's my first contact with a linux OS . I try to install WINE on a AMD64 machine . First I've installed it successfuly from applications -> add remove and after I needed to remove it because I can't upgrade from there... Now I've receiver 21301 errors with all method to install it . I receiver this error when I try to update from terminal using 
sudo apt-get update
sudo apt-get install wine


```

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg  Could not connect to wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused) [IP: 81.171.111.247 80]

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not connect to wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused) [IP: 81.171.111.247 80]

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.


```and from first metod from add remove I receiver:
```
W: Failed to fetch http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.29~winehq0~ubuntu~9.04-0ubuntu2_i386.deb
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused) [IP: 81.171.111.247 80]
```also I've tried from system -> synaptic manager and same errors ...
also I've tried to follow this guide: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) but this errors still persists

please help me to get latest wine !

edit: I tried to restart machine and the problems still persist .
ps: I still have at applications -> wine folder from first my install !

---

### Post by red_spyder on 2009-09-11
Are you sure that your Internet is working properly? From what I'm reading the terminal can't connect to the Ubuntu database

---

### Post by puya4ever on 2009-09-11
first time it works fine but now... (after I've installed some applications like nVidia drivers and others) it crashed... I have dynamic IP , I use router , my connection work right I think...

---

### Post by red_spyder on 2009-09-11
Actually I just got the same message after trying something. I got it by changing the software source. try going to System>Administration>Software Sources and then go to the Third-Party Tab. If there is a WineHQ option, toggle it off.

I hope this helps =}

---

### Post by puya4ever on 2009-09-11
thanks man ! you rock ... it works:D

---

### Post by karlmp on 2009-09-11
don't forget to mark your thread solved

---

### Post by P4man on 2009-09-11
FYI: the wine fileserver (wine.budgetdedicated.com) has been offline quite a bit lately. In fact its still offline right now, and thats the cause of those errors.

---


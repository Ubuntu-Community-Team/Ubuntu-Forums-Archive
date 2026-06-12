---
title: "can not install wine"
date: 2011-08-29
forum: General Help
---

### Post by rajibkudas on 2011-08-29
I tried to install Wine from winehq.org....got following error message when installing 
"W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...lucid5_all.deb]("http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu6%7Elucid5_all.deb")
  404  Not Found [IP: 91.189.92.170 80]


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...ucid5_i386.deb]("http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2-0ubuntu6%7Elucid5_i386.deb")
  404  Not Found [IP: 91.189.92.170 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/po...tu3.2_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7%7Edfsg-1ubuntu3.2_i386.deb")
  404  Not Found [IP: 91.189.92.166 80]

---

### Post by seawolf167 on 2011-08-29
What about

```
sudo apt-get install wine
```

---

### Post by rajibkudas on 2011-09-02
Thanks 4 Rep;y....gotting following message.........

```
su$ sudo apt-get install wine
[sudo] password for rajib: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ttf-symbol-replacement winbind wine1.2
Recommended packages:
  winetricks wisotool
The following NEW packages will be installed:
  ttf-symbol-replacement winbind wine wine1.2
0 upgraded, 4 newly installed, 0 to remove and 36 not upgraded.
Need to get 15.0MB of archives.
After this operation, 99.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe ttf-symbol-replacement 1.2-0ubuntu6~lucid5
  404  Not Found [IP: 91.189.88.40 80]
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe wine1.2 1.2-0ubuntu6~lucid5
  404  Not Found [IP: 91.189.88.40 80]
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main winbind 2:3.4.7~dfsg-1ubuntu3.2
  404  Not Found [IP: 91.189.88.40 80]
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe wine 1.2-0ubuntu6~lucid5
  404  Not Found [IP: 91.189.88.40 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main winbind 2:3.4.7~dfsg-1ubuntu3.2
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu6~lucid5_all.deb  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2-0ubuntu6~lucid5_i386.deb  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.2_i386.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine_1.2-0ubuntu6~lucid5_all.deb  404  Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
do apt-get install wine
```[/QUOTE]

---

### Post by kyletstrand on 2011-09-02
How about
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

Maybe it'll help?

---

### Post by yndesai on 2011-09-03
It seems the links in the package list is pointing to a file which is not there on the server.
Said files are not available at the link location.

If you need to install wine please go to 

[http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/)

download deb files and load it using GEBI installer.

---

### Post by Airvikar on 2011-09-03
download deb files: [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)

---

### Post by rajibkudas on 2011-09-10
> **kyletstrand said:**
> How about
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```Maybe it'll help?

I tries sudo apt-get update.....at the end got following message
"$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory"
and when tried to install wine after that got
"
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "

pls help.....

---

### Post by 3rdalbum on 2011-09-10
> **rajibkudas said:**
> I tries sudo apt-get update.....at the end got following message
"$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory"
and when tried to install wine after that got
"
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "

pls help.....

Don't run more than one package manager at a time; this includes apt-get, Update Manager, Software Center etc.

I'd highly recommend changing to a different mirror for Ubuntu software; I notice you're using the one for India which seems a bit more troublesome than most of the other mirrors.

```
gksudo software-properties-gtk
```

and change the "Download From" popup menu to a different mirror, or the Main Server. When you have done that and you go to close the window, it will ask you if you want to reload the package list; click Reload. Afterwards, you should be able to install Wine.

---


---
title: "Installing wine in ubuntu 9.04"
date: 2010-01-17
forum: General Help
---

### Post by karthick87 on 2010-01-17
How to install wine in ubuntu 9.04?

---

### Post by llamabr on 2010-01-17
```
sudo apt-get install wine
```

If this is your first try at using wine, get ready to be disapointed.  In fact, wine is rarely the correct solution to whatever it is you're trying to do.  Usually, there's a native application that will solve your problem much more effectively.

What are you trying to do?

---

### Post by karthick87 on 2010-01-17
I have tried it gives me the following error....

karthick@Learners-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libopenal1 winbind wine-gecko
The following NEW packages will be installed:
  libopenal1 winbind wine wine-gecko
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 20.9MB of archives.
After this operation, 98.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine wine-gecko
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libopenal1 1:1.4.272-2
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main winbind 2:3.3.2-1ubuntu3
  403 Forbidden
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main wine 1.1.35~winehq0~ubuntu~9.04-0ubuntu1
  403 Forbidden
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main wine-gecko 1.0.0-0ubuntu1
  403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.4.272-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/o/openal-soft/libopenal1_1.4.272-2_i386.deb)  403 Forbidden
Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.35~winehq0~ubuntu~9.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.35~winehq0~ubuntu~9.04-0ubuntu1_i386.deb)  403 Forbidden
Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine-gecko/wine-gecko_1.0.0-0ubuntu1_all.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine-gecko/wine-gecko_1.0.0-0ubuntu1_all.deb)  403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.3.2-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.3.2-1ubuntu3_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by atomizer on 2010-01-17
maybe you can try another server....

Go to system=>Administration=>Software Sources   and change "Download from" to main server.

after that you do ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by karthick87 on 2010-02-13
I have tried another server,and now i have installed wine..Thank You

---


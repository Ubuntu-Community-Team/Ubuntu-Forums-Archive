---
title: "Installing software help"
date: 2011-09-06
forum: General Help
---

### Post by COKEDUDE on 2011-09-06
What is the command you need to use to be able to find new repositories? 

```
 ~ $ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin
Suggested packages:
  ttf-baekmuk ttf-unfonts ttf-unfonts-core ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 74 not upgraded.
Need to get 35.9MB of archives.
After this operation, 102MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  sun-java6-jre sun-java6-bin sun-java6-fonts sun-java6-plugin
Authentication warning overridden.
Err http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-jre 6.20dlj-1ubuntu3
  404  Not Found
Err http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-bin 6.20dlj-1ubuntu3
  404  Not Found
Err http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-fonts 6.20dlj-1ubuntu3
  404  Not Found
Err http://archive.canonical.com/ubuntu/ lucid/partner sun-java6-plugin 6.20dlj-1ubuntu3
  404  Not Found
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-jre_6.20dlj-1ubuntu3_all.deb  404  Not Found
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-bin_6.20dlj-1ubuntu3_i386.deb  404  Not Found
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-fonts_6.20dlj-1ubuntu3_all.deb  404  Not Found
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-plugin_6.20dlj-1ubuntu3_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by Johnb0y on 2011-09-06
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

hope they help!

---

### Post by COKEDUDE on 2011-09-06
The advanced simple answer :). 

```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
sudo aptitude clean
sudo aptitude autoclean
sudo apt-get update
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo aptitude install -f
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by TBABill on 2011-09-06
Easy check is to make sure you enabled the partner repository in Software Sources and then ```
sudo apt-get update
``` After that just install what you need.

---


---
title: "Suns StarOffice Crippled synaptic package manager, Help!"
date: 2010-06-06
forum: General Help
---

### Post by ice_666 on 2010-06-06
Hi,
I'm fairly new to ubuntu so hears the problem.
Firstly im running ubuntu 10.4.
I tried to install staroffice but it uses rpms... no debs.
so i used the program alien to convert the rpms into deb files.
Did'nt have much success.
Infact the only thing it done was give me an error message in synaptic package manager.

Here it is ---> "E: The package ooobasis3.1-core06 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."


ooobasis3.1-core06 comes from ooobasis3.1-core06-3.1.0-9399.i586.rpm

Ive already deleted staroffce and want this problem gone.

How do i fix synaptic package manager to not show this error anymore. until this is fixed i cant install programs or updates.

Please Help.
:confused:

---

### Post by ice_666 on 2010-06-06
If i try and install it normaly which would be --> su and as root sh setup.sh it unpacks it to /var/tmp/unpackstar_office and then go's into the main installer. which fails. this is the errors i recieve from the official sun installer. which is because its RPMs and it says to use alien to convert them to Debs.

i don't care about staroffice. i just want this problem fixed as mentioned above. please help.

---

### Post by Leppie on 2010-06-06
try the following command:
```
sudo apt-get -f install
```

btw, ooo* is the open office suite which you can install from the repos (v3.2 for lucid).

---

### Post by ice_666 on 2010-06-06
[sudo] password for ice: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ooobasis3.1-core06 needs to be reinstalled, but I can't find an archive for it.
ice@ice-desktop:~$

---

### Post by ice_666 on 2010-06-06
ive worked out that.. that file is part of openoffice and also tied into java.
can uninstall java or open office without this fixed.lol

im just gonna format and reload ubuntu stuff this.

wont make this mistake again

---

### Post by Leppie on 2010-06-06
you could check which ooo* packages are already installed:
```
dpkg -l | grep ooo
```

---

### Post by ice_666 on 2010-06-06
ice@ice-desktop:~$ dpkg -l | grep ooo
ii  ooobasis3.1-base                          3.1.0-9399                                             Base module for OpenOffice.org 3.1
ii  ooobasis3.1-binfilter                     3.1.0-9399                                             Legacy filters (e.g. StarOffice 5.2) for Ope
ii  ooobasis3.1-calc                          3.1.0-9399                                             Calc module for OpenOffice.org 3.1
ii  ooobasis3.1-core01                        3.1.0-9399                                             Core module for OpenOffice.org 3.1
ii  ooobasis3.1-core02                        3.1.0-9399                                             Office core module for OpenOffice.org 3.1
ii  ooobasis3.1-core03                        3.1.0-9399                                             Office core module for OpenOffice.org 3.1
ii  ooobasis3.1-core04                        3.1.0-9399                                             Office core module for OpenOffice.org 3.1
ii  ooobasis3.1-core05                        3.1.0-9399                                             Office core module for OpenOffice.org 3.1
iHR ooobasis3.1-core06                        3.1.0-9399

---

### Post by Leppie on 2010-06-06
try this then:
```
sudo apt-get purge ooobasis3.1-* && sudo apt-get --purge autoremove
```

---

### Post by ice_666 on 2010-06-06
ice@ice-desktop:~$ sudo apt-get purge ooobasis3.1-* && sudo apt-get --purge autoremove
[sudo] password for ice: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ooobasis3.1-core06 needs to be reinstalled, but I can't find an archive for it.
ice@ice-desktop:~$

---

### Post by ice_666 on 2010-06-06
its pointless......... i might as well format

---

### Post by ice_666 on 2010-06-06
the RPM build has corruped the systems deb build

---

### Post by ice_666 on 2010-06-06
please....... someone must know how to fix this!

---

### Post by Leppie on 2010-06-06
does the setup.sh script have an uninstall routine?

---

### Post by ice_666 on 2010-06-06
nope

---

### Post by Leppie on 2010-06-06
try like this:
```
sudo apt-get -m purge ooobasis3.1-*
```

---

### Post by ice_666 on 2010-06-06
ice@ice-desktop:~$ sudo apt-get -m purge ooobasis3.1-*
[sudo] password for ice: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ooobasis3.1-core06 needs to be reinstalled, but I can't find an archive for it.
ice@ice-desktop:~$

---

### Post by ahalin on 2010-08-04
I have had the same problem, tried all the steps but still get the dreaded "E: The package ooobasis3.2-core03 needs to be reinstalled, but I can't find an archive for it."

Strangely enough, I can still use OOo 3.2 despite having purged and removed:

```
sudo dpkg --remove --force-remove-reinstreq ooobasis3.2-core
```

and 

```
sudo apt-get purge ooobasis3.2-* && sudo apt-get --purge autoremove
```

Which is REALLY annoying because now I cannot install anything. Please tell me I don't have to reinstall Ubuntu 9.10. [I have an older machine and am already having regular crashes, so don't want to upgrade to 10.04 (which is great by the way, I use it on my home pc) and I don't really like Xubuntu.)

---


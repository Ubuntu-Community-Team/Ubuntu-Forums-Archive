---
title: "ubuntu 9.10 package manager"
date: 2010-01-18
forum: General Help
---

### Post by chrisheadlam on 2010-01-18
when i try to run package manager or do the updates on my system it gives me the same message (E:Malformed line 61 in source list /etc/apt/sources.list (dist), E:the list of sources could not b read)'
Could someone plz help me im verry new to linux be runing it for about 4 days now and im really lost on how to fix it. 
any help would b helpful
chris from illinois

---

### Post by Leppie on 2010-01-18
hi and welcome to the community.
could you please attach the concerning file? you can use the paperclip icon in the post toolbar to attach documents.

---

### Post by kako13 on 2010-01-18
> **chrisheadlam said:**
> when i try to run package manager or do the updates on my system it gives me the same message (E:Malformed line 61 in source list /etc/apt/sources.list (dist), E:the list of sources could not b read)'
Could someone plz help me im verry new to linux be runing it for about 4 days now and im really lost on how to fix it. 
any help would b helpful
chris from illinois

I thinks it might help us if you put your source list.

Use the file browser and go to /etc/apt and rigth click over source.list and open with gedit then put it here.

---

### Post by chrisheadlam on 2010-01-18
I hope this is it. 

/.
/usr
/usr/src
/usr/src/nvidia-96.43.13
/usr/src/nvidia-96.43.13/Makefile
/usr/src/nvidia-96.43.13/Makefile.kbuild
/usr/src/nvidia-96.43.13/Makefile.nvidia
/usr/src/nvidia-96.43.13/README
/usr/src/nvidia-96.43.13/conftest.sh
/usr/src/nvidia-96.43.13/cpuopsys.h
/usr/src/nvidia-96.43.13/gcc-version-check.c
/usr/src/nvidia-96.43.13/makefile
/usr/src/nvidia-96.43.13/nv-i2c.c
/usr/src/nvidia-96.43.13/nv-kernel.o
/usr/src/nvidia-96.43.13/nv-linux.h
/usr/src/nvidia-96.43.13/nv-memdbg.h
/usr/src/nvidia-96.43.13/nv-misc.h
/usr/src/nvidia-96.43.13/nv-vm.c
/usr/src/nvidia-96.43.13/nv-vm.h
/usr/src/nvidia-96.43.13/nv.c
/usr/src/nvidia-96.43.13/nv.h
/usr/src/nvidia-96.43.13/nvreadme.h
/usr/src/nvidia-96.43.13/nvtypes.h
/usr/src/nvidia-96.43.13/os-agp.c
/usr/src/nvidia-96.43.13/os-agp.h
/usr/src/nvidia-96.43.13/os-interface.c
/usr/src/nvidia-96.43.13/os-interface.h
/usr/src/nvidia-96.43.13/os-registry.c
/usr/src/nvidia-96.43.13/patches
/usr/src/nvidia-96.43.13/patches/nvidia-rt-compat-legacy.patch
/usr/src/nvidia-96.43.13/patches/fall_back_on_mtrr_if_no_pat.patch
/usr/src/nvidia-96.43.13/patches/rt_preempt_31.patch
/usr/src/nvidia-96.43.13/rmretval.h
/usr/src/nvidia-96.43.13/dkms.conf
/usr/share
/usr/share/doc
/usr/share/doc/nvidia-96-kernel-source
/usr/share/doc/nvidia-96-kernel-source/NEWS.Debian.gz
/usr/share/doc/nvidia-96-kernel-source/README.txt.gz
/usr/share/doc/nvidia-96-kernel-source/README.Debian
/usr/share/doc/nvidia-96-kernel-source/copyright
/usr/share/doc/nvidia-96-kernel-source/changelog.Debian.gz
/usr/share/doc/nvidia-96-kernel-source/NVIDIA_Changelog.gz

---

### Post by Leppie on 2010-01-18
the exact location (path + filename) of the file is this: /etc/apt/sources.list
could you please post this file?

---

### Post by michy99 on 2010-01-18
The problem is in the file /etc/apt/sources.list. If you will post the contents of that file we can tell you how to fix it.

---

### Post by chrisheadlam on 2010-01-18
I open up places and then search for files and type in  /etc/apt/sources.list in look in folder i put in file system and it says no files found. what am i doing wrong. sorry for being so stupied to linux im verry new.

---

### Post by HeadHunter00 on 2010-01-18
Open terminal(accessories->terminal) and > sudo gedit /etc/apt/sources.list and then check for errors or delete the 61st line. After that > sudo apt-get update in terminal

---

### Post by chrisheadlam on 2010-01-18
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu)
sudo gedit /etc/apt/sources.list karmic main

---

### Post by Leppie on 2010-01-18
follow HeadHunter00's instructions
delete line 61, which is the following:
```
deb [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
```
save the file and exit and run:
```
sudo apt-get update
```

---

### Post by chrisheadlam on 2010-01-18
E: Malformed line 61 in source list /etc/apt/sources.list (dist)
Thats what i get when i type in sudo apt-get update in terminal

---

### Post by chrisheadlam on 2010-01-18
when i deleted line 61 then saved it

---

### Post by michy99 on 2010-01-18
If the last line of the file is```
sudo gedit /etc/apt/sources.list karmic main
```Then it should not be there. Delete that line.

---

### Post by chrisheadlam on 2010-01-18
I did that and it still gives me the same error this is what i have. 

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu)

---

### Post by michy99 on 2010-01-18
Change this last part```

## Beryl repository
deb http://ubuntu.beryl-project.org/ edgy main

## Beryl repository
deb http://ubuntu.beryl-project.org/ edgy main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu
```to this:```
## Beryl repository
deb http://ubuntu.beryl-project.org/ karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
```Save and try updating.

---

### Post by chrisheadlam on 2010-01-18
now it says E: Malformed line 58 in source list /etc/apt/sources.list (dist)
this is what i have now.

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


## Beryl repository
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu)

---

### Post by chrisheadlam on 2010-01-18
Sorry i have that last part wrong thanks for the help guys.
i updated and this is what it says

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic Release.gpg                         
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Get:8 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]                     
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic Release                             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [65.9kB]                     
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic/main Packages                       
Get:10 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [3,405B]           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic/main Packages                       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]            
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [49.2kB]       
Get:13 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources [1,390B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Err [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) karmic/main Packages                       
  403  Forbidden
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [2,280B]                  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [1,353kB]           
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [14.0kB]       
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [21.1kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [3,944B]    
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [575B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [7,971B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [640kB]                
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [3,270B]         
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [5,133kB]         
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [190kB]         
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources [116kB]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [142kB]       
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [44.5kB]       
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [87.2kB]  
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [21.2kB]   
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B] 
Fetched 10.9MB in 36s (299kB/s)                                                
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: Failed to fetch [http://ubuntu.beryl-project.org/dists/karmic/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/karmic/main/binary-i386/Packages.gz)  403  Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by chrisheadlam on 2010-01-18
that u guys u were very helpful. 
is there any books out there that will help with this kinda of stuff and linux in general.
if u meet any of u guys in real life i owe u lunch thanks again

---

### Post by Leppie on 2010-01-18
execute the following command (copy & paste into terminal):
```
[FONT=courier new,courier]sudo apt-get update 2> /tmp/keymissing; for key in $(grep "NO_PUBKEY" /tmp/keymissing |sed "s/.*NO_PUBKEY //"); do echo -e "\nProcessing key: $key"; gpg –keyserver subkeys.pgp.net –recv $key && gpg –export –armor $key | sudo apt-key add -; done[/FONT]
```

---


---
title: "cant install k3b"
date: 2009-11-10
forum: General Help
---

### Post by sdowney717 on 2009-11-10
is it fixable?

> scott@scott-desktop:~/Videos$ sudo apt-get install k3b
Reading package lists... Done


Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdebase-runtime (>= 4:4.3.2) but it is not going to be installed
       Depends: libk3b6 but it is not going to be installed
       Depends: libkcddb4 (>= 4:4.2.96) but it is not going to be installed
       Depends: kdebase-workspace-bin but it is not going to be installed
E: Broken packages
scott@scott-desktop:~/Videos$ 

---

### Post by dragonboss on 2009-11-10
Try installing k3b from the ubuntu software center(previously add/remove programs) or synaptic package manager

---

### Post by sdowney717 on 2009-11-10
more complex than this

---

### Post by dragonboss on 2009-11-10
Have you tried installing the dependencies one by one from synaptic?
Plus, in synaptic search for k3b right click and dependencies tab lists all dependencies

---

### Post by oldos2er on 2009-11-10
> **dragonboss said:**
> Try installing k3b from the ubuntu software center(previously add/remove programs) or synaptic package manager

 Check to make sure you have all repositories enabled. If so, run ```
sudo-apt-get update && sudo apt-get install k3b
```
If you see errors from this command, please copy and paste them here.

---

### Post by sdowney717 on 2009-11-10
actually, that might work
But i dont want to downgrade nvidia driver from 190 to 185
that is my video driver

> scott@scott-desktop:~$ sudo apt-get update && sudo apt-get install k3b
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US  
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources
Fetched 616B in 1s (413B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BBD133164234534
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1DABDBB4CEC06767
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_karmic_non-free_binary-i386_Packages)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akonadi-server exiv2 k3b-data kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdelibs-bin
  kdelibs5 kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4
  kdepimlibs-data kdepimlibs5 khelpcenter4 libakonadiprivate1
  libboost-program-options1.38.0 libclucene0ldbl libexiv2-5 libflac++6 libk3b6
  libkcddb4 libknotificationitem1 liblzma0 libplasma3 libpolkit-qt0
  libqimageblitz4 libqt4-opengl libqt4-qt3support libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libxcb-shape0 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  mysql-server-core-5.1 nvidia-185-libvdpau phonon-backend-xine
  plasma-dataengines-workspace plasma-widgets-workspace soprano-daemon
Suggested packages:
  normalize-audio toolame movixmaker-2 vcdimager kdebase-kio-plugins kdebase
  djvulibre-bin plasma-scriptengines gxine xine-ui libxine1-doc libxine-doc
  libxine1-ffmpeg
The following packages will be REMOVED:
  nvidia-190-libvdpau nvidia-glx-190
The following NEW packages will be installed:
  akonadi-server exiv2 k3b k3b-data kde-icons-oxygen kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdelibs-bin
  kdelibs5 kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4
  kdepimlibs-data kdepimlibs5 khelpcenter4 libakonadiprivate1
  libboost-program-options1.38.0 libclucene0ldbl libexiv2-5 libflac++6 libk3b6
  libkcddb4 libknotificationitem1 liblzma0 libplasma3 libpolkit-qt0
  libqimageblitz4 libqt4-opengl libqt4-qt3support libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libxcb-shape0 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x
  mysql-server-core-5.1 nvidia-185-libvdpau phonon-backend-xine
  plasma-dataengines-workspace plasma-widgets-workspace soprano-daemon
0 upgraded, 51 newly installed, 2 to remove and 10 not upgraded.
Need to get 2,952kB/68.0MB of archives.
After this operation, 156MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
scott@scott-desktop:~$ 


---

### Post by dragonboss on 2009-11-10
Hmm, the first thing that comes to mind is removing it temporarily, installing k3b then putting it back, but i'm not sure if that will work....

---

### Post by oldos2er on 2009-11-12
"The following packages will be REMOVED:
nvidia-190-libvdpau nvidia-glx-190"

 That's very strange. I can think of no reason offhand why apt would want to do that, unless there's a poorly put together package somewhere.

---

### Post by sdowney717 on 2009-11-13
[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+packages)

this is the launchpad ppa for nvidia 190

---

### Post by sdowney717 on 2009-11-28
I just tried it again and it installed with no grief. still using the 190 drivers

---


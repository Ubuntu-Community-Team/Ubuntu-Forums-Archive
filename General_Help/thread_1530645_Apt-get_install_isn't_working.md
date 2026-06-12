---
title: "Apt-get install isn't working"
date: 2010-07-13
forum: General Help
---

### Post by Bradj47 on 2010-07-13
Title says it all. Here's the output I get when I try apt-get installing something: 

```
resuni@resuni-netbook:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liblzo2-2 libmp3lame0 libsvga1 libxvidcore4
Suggested packages:
  mplayer-doc netselect fping
The following NEW packages will be installed:
  liblzo2-2 libmp3lame0 libsvga1 libxvidcore4 mplayer
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,899kB of archives.
After this operation, 7,795kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  liblzo2-2 libmp3lame0 libsvga1 libxvidcore4 mplayer
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main liblzo2-2 2.03-2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse libmp3lame0 3.98.2+debian-0ubuntu3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe libsvga1 1:1.4.3-29
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe libxvidcore4 2:1.2.2+debian-0ubuntu2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse mplayer 2:1.0~rc3+svn20090426-1ubuntu16
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lzo2/liblzo2-2_2.03-2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/libmp3lame0_3.98.2+debian-0ubuntu3_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/svgalib/libsvga1_1.4.3-29_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.2.2+debian-0ubuntu2_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu16_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
resuni@resuni-netbook:~$ 

```

Then when I run apt-get update --fix-missing as it suggests: 

```
resuni@resuni-netbook:~$ sudo apt-get update --fix-missing
Err http://security.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                                            
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com lucid Release.gpg                                     
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com lucid-security Release                                  
Ign http://security.ubuntu.com lucid-security/main Packages                            
Ign http://security.ubuntu.com lucid-security/restricted Packages                      
Ign http://security.ubuntu.com lucid-security/main Sources                             
Ign http://security.ubuntu.com lucid-security/restricted Sources                       
Err http://www.lxtec.de unstable Release.gpg                                           
  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)
Err http://www.lxtec.de/debarchiv/ unstable/main Translation-en_US                     
  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)
Err http://dl.google.com/linux/deb/ stable/main Translation-en_US                      
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US               
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid Release.gpg                                     
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US       
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US   
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates Release.gpg                  
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com lucid-security/universe Packages             
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://www.lxtec.de unstable Release
Ign http://dl.google.com stable Release
Ign http://us.archive.ubuntu.com lucid Release
Ign http://us.archive.ubuntu.com lucid-updates Release
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://archive.canonical.com lucid Release
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/restricted Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://www.lxtec.de unstable/main Packages
Ign http://dl.google.com stable/main Packages
Ign http://us.archive.ubuntu.com lucid/main Packages
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://archive.canonical.com lucid/partner Packages
Err http://security.ubuntu.com lucid-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/universe Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://www.lxtec.de unstable/main Sources
Ign http://dl.google.com stable/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://archive.canonical.com lucid/partner Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://www.lxtec.de unstable/main Packages
Err http://dl.google.com stable/main Packages
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Err http://archive.canonical.com lucid/partner Packages
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://www.lxtec.de unstable/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com lucid/main Packages
Err http://www.lxtec.de unstable/main Packages
  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com lucid/restricted Packages
Ign http://us.archive.ubuntu.com lucid/main Sources
Err http://www.lxtec.de unstable/main Sources
  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com lucid/restricted Sources
Ign http://us.archive.ubuntu.com lucid/universe Packages
Ign http://us.archive.ubuntu.com lucid/universe Sources
Ign http://us.archive.ubuntu.com lucid/multiverse Packages
Ign http://us.archive.ubuntu.com lucid/multiverse Sources
Ign http://us.archive.ubuntu.com lucid-updates/main Packages
Ign http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://us.archive.ubuntu.com lucid-updates/main Sources
Ign http://us.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://us.archive.ubuntu.com lucid-updates/universe Packages
Ign http://us.archive.ubuntu.com lucid-updates/universe Sources
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://us.archive.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com lucid-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.lxtec.de/debarchiv/dists/unstable/Release.gpg  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.lxtec.de/debarchiv/dists/unstable/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.lxtec.de/debarchiv/dists/unstable/main/binary-i386/Packages.gz  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.lxtec.de/debarchiv/dists/unstable/main/source/Sources.gz  Something wicked happened resolving 'www.lxtec.de:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
resuni@resuni-netbook:~$ 

```

Here is my /etc/apt/sources.list file if needed: 

```
resuni@resuni-netbook:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://www.lxtec.de/debarchiv unstable main
deb-src http://www.lxtec.de/debarchiv unstable main
resuni@resuni-netbook:~$ 

```

---

### Post by belkinsa on 2010-07-13
Did you update your netbook?

---

### Post by snowpine on 2010-07-13
Try:

```
sudo apt-get update
```

Also sometimes one of the mirrors has problems; you could try a different mirror, or just wait a little while. :)

---

### Post by belkinsa on 2010-07-13
Or you could go to System>Administration>Update Manager

---

### Post by Bradj47 on 2010-07-13
The results of sudo apt-get update are in my first post. When I use the graphical approach and use the System -> Administration -> Update Manager as you suggest, I get an error (see attached screenshot). My desktop computer has a similar problem. Except my desktop computer has a warning sign in the system tray that says the update information is outdated. I can not update nor install any packages using apt-get. How do I fix this?

---

### Post by CharlesA on 2010-07-13
Try a different mirror.

---

### Post by dmizer on 2010-07-13
It appears as though these two repositories are causing you problems:
```
deb http://www.lxtec.de/debarchiv unstable main
deb-src http://www.lxtec.de/debarchiv unstable main
```

Those archives do not exist any longer. Comment them out, and try again.

---

### Post by Bradj47 on 2010-07-13
> **dmizer said:**
> It appears as though these two repositories are causing you problems:
```
deb http://www.lxtec.de/debarchiv unstable main
deb-src http://www.lxtec.de/debarchiv unstable main
```

Those archives do not exist any longer. Comment them out, and try again.

That fixed it. Thanks a lot!

---

### Post by belkinsa on 2010-07-13
Don't forget to mark this "SOLVED"

---


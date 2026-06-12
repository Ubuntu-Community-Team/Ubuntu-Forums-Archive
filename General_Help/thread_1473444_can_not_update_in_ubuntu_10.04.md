---
title: "can not update in ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by bilol on 2010-05-05
hi all,
*sudo apt-get update* is not working sometimes.I am getting the following error. Please help...

```
dhiman@dhiman-desktop:~$ sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Hit http://archive.getdeb.net lucid-getdeb Release.gpg                        
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_IN     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com lucid-security Release                         
Hit http://archive.getdeb.net lucid-getdeb Release                             
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.getdeb.net lucid-getdeb/apps Packages                      
Hit http://security.ubuntu.com lucid-security/restricted Packages             
Hit http://security.ubuntu.com lucid-security/main Sources                    
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources              
Err http://in.archive.ubuntu.com lucid Release.gpg                            
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.34). - connect (110: Connection timed out)
Err http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Ign http://in.archive.ubuntu.com lucid Release
Ign http://in.archive.ubuntu.com lucid-updates Release
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/universe Sources 
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/universe Sources
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://in.archive.ubuntu.com lucid/main Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/universe Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err http://in.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to in.archive.ubuntu.com:80 (111.91.91.34). - connect (110: Connection timed out)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to in.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

 

```

---

### Post by bilol on 2010-05-05
SOLVED...
I got the solution [here]("http://ubuntuforums.org/showthread.php?t=94111")

---

### Post by konjeng on 2010-05-08
could you send me the sources.list file please i have same problem
i would be thankful if u do

---

### Post by lidex on 2010-05-08
That looks like a connection issue with the server. You can always specify another one. Go to 'System>Administration>Software Sources' and click on the dropdown box next to 'Download from'. You'll have options to select a different server there.

---

### Post by bilol on 2010-05-10
Dear konjeng here is the output:

```
dhiman@dhiman-desktop:~$ sudo cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[APTonCD for ubuntu lucid - i386 (2010-05-06 14:13) DVD1]/ /
deb http://in.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid universe
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

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
deb http://archive.canonical.com/ lucid partner



```

---

### Post by ds77 on 2010-05-27
I seem to be having a similar problem.  It doesn't matter what network connection I am on, either wireless or hardwired from home or work, I get the following errors when trying to update.

I am a bit of a newbie to full time Ubuntu and only gone "all the way" when Karmic came out, so im lost in this.  I have tried different servers with no luck.  I see the post that apparently can fix this problem, but it seems I need a new source.list, Any ideas?    thanks!

```

Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) karmic/ Release.gpg
Ign [http://repo.ahadiel.org/apt/](http://repo.ahadiel.org/apt/) karmic/ Translation-en_US                     
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) lucid/ Release.gpg                                 
Hit [http://www.fbreader.org](http://www.fbreader.org) stable Release.gpg                                 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://repo.ahadiel.org/apt/](http://repo.ahadiel.org/apt/) lucid/ Translation-en_US                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) karmic/ Release                                    
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) lucid/ Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) karmic/ Packages                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) lucid/ Packages                                    
Ign [http://www.fbreader.org/desktop/debian/](http://www.fbreader.org/desktop/debian/) stable/main Translation-en_US      
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) karmic/ Packages                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,051B]                       
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://repo.ahadiel.org](http://repo.ahadiel.org) lucid/ Packages                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://www.fbreader.org](http://www.fbreader.org) stable Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://repo.ahadiel.org](http://repo.ahadiel.org) karmic/ Packages                                   
Hit [http://repo.ahadiel.org](http://repo.ahadiel.org) lucid/ Packages                                    
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Packages                               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_US   
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ppa.launchpad.net/chuchiperriman/cloudsn/ubuntu/](http://ppa.launchpad.net/chuchiperriman/cloudsn/ubuntu/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources                                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://ppa.launchpad.net/user/ppa-name/ubuntu/](http://ppa.launchpad.net/user/ppa-name/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                            
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Sources
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Err [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources
  Unable to connect to archive.getdeb.net:http:
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
  Unable to connect to archive.getdeb.net:http:
Fetched 10.8kB in 21s (516B/s)
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-amd64/Packages.gz)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/source/Sources.gz)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-amd64/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-amd64/Packages.gz)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by jerenept on 2010-05-27
GetDeb server appears to be down. Disable it in  Software Sources.

---

### Post by ds77 on 2010-05-27
Now I get it.  Simple as that.  Thanks jerenept!

---


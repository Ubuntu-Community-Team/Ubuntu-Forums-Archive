---
title: "updating error"
date: 2011-07-24
forum: General Help
---

### Post by Jonah Svanberg on 2011-07-24
Hi I have try'd to look for solution to this update error on the internet but i could'nt find any, I thought i might be a dropbox error so i try'd to reinstall it, but i still have same error. I hope someone can help me out.
Here are my update log:
       
user@ubuntu:~$ sudo apt-get update
Err [http://ararchive.canonical.com](http://ararchive.canonical.com) lucid Release.gpg
  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://ararchive.canonical.com/](http://ararchive.canonical.com/) lucid/partner Translation-en_GB            
  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://ararchive.canonical.com](http://ararchive.canonical.com) lucid Release                               
Ign [http://ararchive.canonical.com](http://ararchive.canonical.com) lucid/partner Packages                      
Ign [http://ararchive.canonical.com](http://ararchive.canonical.com) lucid/partner Packages                      
Err [http://ararchive.canonical.com](http://ararchive.canonical.com) lucid/partner Packages                      
  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/libv4l/ppa/ubuntu/](http://ppa.launchpad.net/libv4l/ppa/ubuntu/) lucid/main Translation-en_GB   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                       
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
W: Failed to fetch [http://ararchive.canonical.com/dists/lucid/Release.gpg](http://ararchive.canonical.com/dists/lucid/Release.gpg)  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ararchive.canonical.com/dists/lucid/partner/i18n/Translation-en_GB.bz2](http://ararchive.canonical.com/dists/lucid/partner/i18n/Translation-en_GB.bz2)  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ararchive.canonical.com/dists/lucid/partner/binary-amd64/Packages.gz](http://ararchive.canonical.com/dists/lucid/partner/binary-amd64/Packages.gz)  Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2011-07-25
> W: Failed to fetch [http://ararchive.canonical.com/dists/lucid/Release.gpg](http://ararchive.canonical.com/dists/lucid/Release.gpg) Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ararchive.canonical.com/dists...tion-en_GB.bz2](http://ararchive.canonical.com/dists...tion-en_GB.bz2) Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ararchive.canonical.com/dists...64/Packages.gz](http://ararchive.canonical.com/dists...64/Packages.gz) Something wicked happened resolving 'ararchive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead. 

**'ararchive** that doesn't look right in your sources.list.

Can you post your sources.list

From a terminal ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by Jonah Svanberg on 2011-07-25
Yes here is it:

user@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

# libv4l PPA
deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) lucid main
deb [http://ararchive.canonical.com/](http://ararchive.canonical.com/) lucid partner

---

### Post by raja.genupula on 2011-07-25
better to update again by removing the broken index

```
sudo rm -rf /var/lib/apt/lists/*
``````

sudo apt-get update
```

---

### Post by gmargo on 2011-07-25
> **Jonah Svanberg said:**
> 
deb [http://[COLOR=Red]ararchive[/COLOR].canonical.com/]("http://ararchive.canonical.com/") lucid partner

It's the very last line.  Should be "archive" instead of "ararchive".

---

### Post by Jonah Svanberg on 2011-07-25
Ah i fixed it, i run the sources.list as sudo user then change the last line from 

deb [http://ararchive.canonical.com/](http://ararchive.canonical.com/) lucid partner

to:


deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

that solved the issue. Thanks for the idea about the source list :)

---


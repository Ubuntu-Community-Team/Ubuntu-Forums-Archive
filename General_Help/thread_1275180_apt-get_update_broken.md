---
title: "apt-get update broken"
date: 2009-09-25
forum: General Help
---

### Post by primowalker on 2009-09-25
Here is what happens when I run apt-get update.  Nothing has changed on this system since the last successful update.

jpwalker@obiwan:~$ sudo apt-clean
jpwalker@obiwan:~$ sudo apt-autoclean
jpwalker@obiwan:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
99% [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                         
  Sub-process bzip2 returned an error code (2)
99% [2 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                         
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                                   
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                        
99% [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                   
  Sub-process bzip2 returned an error code (2)
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
99% [4 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages  
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
99% [5 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources        
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
99% [6 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources  
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
99% [7 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages    
  Sub-process bzip2 returned an error code (2)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
99% [8 Sources bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources    
  Sub-process bzip2 returned an error code (2)
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages    
99% [9 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages       
  Sub-process bzip2 returned an error code (2)
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
99% [10 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
  Sub-process bzip2 returned an error code (2)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
99% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages  
  Sub-process bzip2 returned an error code (2)
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources 
99% [12 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
99% [13 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
99% [14 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
  Sub-process bzip2 returned an error code (2)
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
99% [15 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
  Sub-process bzip2 returned an error code (2)
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
99% [16 Sources bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
  Sub-process bzip2 returned an error code (2)
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
99% [17 Packages bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
99% [18 Sources bzip2 0]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Fetched 46.5kB in 4s (9955B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/main/source/Sources.bz2](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


Here is my /etc/apt/sources.list file:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

#Chromium Repositories
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

---

### Post by Liolikas on 2009-09-25
This may happen if you hit repository update time well with system update. Try later if no luck post more.

---

### Post by primowalker on 2009-09-25
This has been happening for two days now.

---

### Post by wojox on 2009-09-25
I've been having this problem as well. Even tried changing servers. I think the U.S. servers are out of sync.

---

### Post by zaduma on 2009-09-25
try running aptitude... maybe somehow apt-get is broken.

sudo aptitude update

---

### Post by drs305 on 2009-09-25
As was mentioned, the server may have just be down temporarily. I substituted your sources.list for mine and it ran fine. The only message I got out of the ordinary was I didn't have one public key you did, which would be expected.

Try again and let us know if you are still having problems. If not, please mark the thread SOLVED via the "thread tools" link at the top right of the first post.

---

### Post by wojox on 2009-09-25
Okay, tried running it again with same errors. Then tried :

```
sudo apt-get update && sudo apt-get upgrade
```

Everything worked. Strange.....

---

### Post by primowalker on 2009-09-26
I tired all of the above.  I also other server from the US, Canada and the UK and still get the same errors.

---

### Post by drs305 on 2009-09-26
> **primowalker said:**
> I tired all of the above.  I also other server from the US, Canada and the UK and still get the same errors.

I just reloaded your sources.list again and it worked properly. I suspect it is a problem with either the way you are connecting to the repositories or a bad file(s).

Open Synaptic, Settings, Repositories and note which ones you have enabled in the Ubuntu Software and Third Party/Other tab. Untick them all and then Reload. This will clear the listings in /var/lib/dpkg/lists. Then reselect the repositories and Reload again. This should refresh the list and replace any lists which were bad.

You could also run this to clear the list of available packages:
```

sudo dpkg --clear-avail

```

---

### Post by dapaintballer331 on 2010-03-21
drs305, you fixed the problem for me! Thanks a lot.

PS: People should probably NOT re-enable these repos: Google code/software, chromium, chromium source

---

